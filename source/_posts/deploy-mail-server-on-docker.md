---
title: Docker架設郵件伺服器
id: deploy-mail-server-on-docker
author: Yi-Min Cai
mathjax: false
date: 2020-05-28 16:40:46
categories: Docker
tags:
    - Docker
    - Docker Compose
    - Mail Server
    - SMTP
    - IMAP
    - POP3
---
# 摘要

今天我們使用[tomav/docker-mailserver](https://github.com/tomav/docker-mailserver)所提供的Docker Image來快速的架設一個簡單的Mail Server。

<!-- more -->

# 基礎知識

**常見的郵局埠與通訊協議**

發郵件的協議有SMTP，收郵件的協議有POP3和IMAP。

- **SMTP**：明文使用25埠。加密後使用25/587/465埠。
- **IMAP**：明文使用143埠。加密後使用143/993埠。
- POP3：明文使用110埠。加密後使用110/995埠。

這次使用的Docker映像檔為：tvial/docker-mailserver

- 參考連結
  - [Github tvail/docker-mailserver](https://github.com/tomav/docker-mailserver)
  - [Install example](https://github.com/tomav/docker-mailserver/wiki/Setup-docker-mailserver-using-the-script-setup.sh)
  - [docker-mailserver Github Wiki](https://github.com/tomav/docker-mailserver/wiki)
  - [利用Docker自建多功能加密邮件服务器](https://www.itmanbu.com/docker-mail-server.html)

確保您有安裝[Docker](https://www.docker.com/)、[Docker-Compose](https://docs.docker.com/compose/install/) 1.7 or higher

**本服務所使用的連接埠：**

#### Exposed ports

- 25 receiving email from other mailservers
- 465 SSL Client email submission
- 587 TLS Client email submission
- 143 StartTLS IMAP client
- 993 TLS/SSL IMAP client
- 110 POP3 client
- 995 TLS/SSL POP3 client

```
Note: Port 25 is only for receiving email from other mailservers and not for submitting email. You need to use port 465 or 587 for this.
```

# Usage

1. **從Docker Hub pull 映像檔**

```bash
$ docker pull tvial/docker-mailserver:latest
```

2. **Get tools, docker-compose.yml, the .env and the setup.sh files: **

```bash
$ curl -o setup.sh https://raw.githubusercontent.com/tomav/docker-mailserver/master/setup.sh

$ chmod a+x ./setup.sh

$ curl -o docker-compose.yml https://raw.githubusercontent.com/tomav/docker-mailserver/master/docker-compose.yml.dist

$ curl -o .env https://raw.githubusercontent.com/tomav/docker-mailserver/master/.env.dist

```

***Note***:在這裡我找到一個問題，docker-compose.yml 檔案中第20行引入了"env-mailserver"，但在作者的README.MD、參數說明文件中並未找到此檔案說明。

下載來的 docker-compose.yml：

```bash
version: '2'
services:
  mail:
    image: tvial/docker-mailserver:latest
    hostname: ${HOSTNAME}
    domainname: ${DOMAINNAME}
    container_name: ${CONTAINER_NAME}
    ports:
    - "25:25"
    - "143:143"
    - "587:587"
    - "993:993"
    volumes:
    - maildata:/var/mail
    - mailstate:/var/mail-state
    - maillogs:/var/log/mail
    - ./config/:/tmp/docker-mailserver/
    env_file:
    - .env
    - env-mailserver
    cap_add:
    - NET_ADMIN
    - SYS_PTRACE
    restart: always
volumes:
  maildata:
    driver: local
  mailstate:
    driver: local
  maillogs:
    driver: local
```

修改後的 docker-compose.yml：

```bash
version: '2'

services:
  mail:
    image: tvial/docker-mailserver:latest
    hostname: mail
    domainname: mail.nemu.edu.tw
    container_name: mail
    ports:
      - "25:25"
      - "143:143"
      - "587:587"
      - "993:993"
    volumes:
      - /home/mail:/var/mail
      - /home/mail-state:/var/mail-state
      - /root/config/:/tmp/docker-mailserver/
      - /etc/letsencrypt:/etc/letsencrypt
    environment:
      - ENABLE_SPAMASSASSIN=0
      - ENABLE_CLAMAV=0
      - ENABLE_FAIL2BAN=1
      - ONE_DIR=1
      - DMS_DEBUG=0
      - SSL_TYPE=letsencrypt
    cap_add:
      - NET_ADMIN
```

請注意修改後文件的6、7行，hostname+domainname=完整域名，另外，在本次修改的設定檔中，將兩個服務關閉了，分別是ENABLE_SPAMASSASSIN、ENABLE_CLAMAV，

# Add mail server user accont

```bash
$ mkdir -p /root/config
$ touch /root/config/postfix-accounts.cf
$ docker run --rm \
 -e MAIL_USER=apple@app.nemu.edu.tw \
 -e MAIL_PASS=123456 \
 -ti tvial/docker-mailserver:latest \
 /bin/sh -c 'echo "$MAIL_USER|$(doveadm pw -s SHA512-CRYPT -u $MAIL_USER -p $MAIL_PASS)"' >> /root/config/postfix-accounts.cf
```

# 建立DKIM Key

```bash
$ docker run --rm \
 -v "/root/config":/tmp/docker-mailserver \
 -ti tvial/docker-mailserver:latest generate-dkim-config
```

執行完之後查看/root/config/opendkim/keys/**mail.nemu.edu.tw**/mail.txt的內容就是我們要設定的dns解析。我的內容是：

```bash
$ cat /root/config/opendkim/keys/mail.nemu.edu.tw/mail.txt
mail._domainkey IN TXT ( "v=DKIM1; k=rsa; "
"p=MIGfMA0GCSqGSIb3DPENNNNNNNNNNCBiQKBgQCy9JV3FnXjLjsRJs/N0fy1C233333IV7t3f7fWpv/lo4NsoPEtG693hTgApkhuLl9KeV233333DMTagtXN898lXenKFEIS4COi7X/RjbGuOoApg4qS23333333TfXsrjN3xVC78E9T/HrS6pJN5fX+1s+1s+1s+1s+1s+1sIDAQAB" ) ; ----- DKIM key mail for mail.nemu.edu.tw
```

因為是自己搭建的bind直接把這段複製到OS裡的hosts檔案內就行了，如下圖直接貼上儲存。

Ex. MacOS、Linux的檔案位置如下：

```bash
# MacOS:
/private⁩/⁨etc⁩/hosts
# Linux(CentOS 7):
/etc/hosts
```

{% asset_img bind-rsa-in-hosts.png %}

# 建立SSL

```bash
$ cd ~/mail/docker-mailserver/
$ ./setup.sh config ssl
```



# 啟動Docker容器

確認防火牆有開啟郵件伺服器所需的通訊埠號，在CentOS中使用firewalld作為預設防火牆。

```bash
# 確認目前設定
$ firewall-cmd --list-all

# 加入自行指定的連接埠
$ firewall-cmd --add-port=25/tcp --permanent
$ firewall-cmd --add-port=143/tcp --permanent
$ firewall-cmd --add-port=465/tcp --permanent
$ firewall-cmd --add-port=587/tcp --permanent
$ firewall-cmd --add-port=993/tcp --permanent

# 重新載入設定
$ firewall-cmd --reload

### 關閉防火牆服務(optional)
$ systemctl stop firewall
$ systemctl disable firewall
```

啟動Docker容器

```bash
# 背景執行
$ docker-compose up -d mail
```

or

```bash
# view process
$ docker-compose up mail
```

# **測試SSL設定是否成功**

```bash
$ docker exec mail openssl s_client -connect 0.0.0.0:587 -starttls smtp -CApath /etc/letsencrypt/
```

和

```bash
$ docker exec mail openssl s_client -connect 0.0.0.0:993 -starttls imap -CApath /etc/letsencrypt/
```

若能看到以下結果，代表成功了。

```
Ｖerify return code: 0 (ok)
```

# **Client端連線設定**

收信：

- Server domain name：mail.nemu.edu.tw
- Protocol：IMAP
- Port：993
- Use SSL：是

發信：

- Server domain name：mail.nemu.edu.tw
- Protocol：SMTP
- Port：587
- Use SSL：是

<!-- 目前已新增兩個使用者：

- Neil
  - User Name：neil@mail.nemu.edu.tw
  - Password：123456

- Edward
  - User Name：edward@mail.nemu.edu.tw
  - Password：123456 -->

# **測試結果**

{% asset_img test-result.jpg %}

