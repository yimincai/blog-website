---
title: SSH連線出現錯誤 WARNING REMOTE HOST IDENTIFICATION HAS CHANGED!
id: ssh-warning-remote-host-identification-has-changed
author: Yi-Min Cai
mathjax: false
date: 2020-06-05 20:02:44
categories: Openssh
tags: 
    - Openssh server
    - Linux
---
# 摘要

當在使用SSH連線到別台主機時若出現以下錯誤可參考以下解決方式。

<!-- more -->

錯誤訊息：

```bash
[neil@yimincai.net ~]$ ssh alyssa@192.168.50.6
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
48:0e:28:11:d6:81:68:16:04:5f:db:49:02:la:12:4e.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:12
RSA host key for 192.168.50.6 has changed and you have requested strict checking.
Host key verification failed.
```

解決方法（擇一即可）：

## 1. 把有問題的host key刪掉

```bash
vim /neil/.ssh/known_hosts
```

## 2. 刪除known_hosts

```bash
rm -rf  /neil/.ssh/known_hosts
```

## 3. 重新產生key

```bash
ssh-keygen -R 192.168.50.6
```