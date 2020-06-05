---
title: Install openssh-server on Ubuntu and ssh usage
id: install-openssh-server-on-ubuntu-and-ssh-usage
author: Yi-Min Cai
mathjax: false
date: 2020-06-05 19:10:28
categories: Openssh
tags:
    - Ubuntu
    - Openssh server
---

# Install openssh

Update first

```bash
sudo apt-get update -y
```
<!-- more -->

Install openssh-server

```bash
sudo apt install openssh-server -y
```

![install-openssh-server](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-openssh-server-on-ubuntu-and-ssh-usage%2Finstall-openssh-server.png?alt=media&token=fd75beab-37c9-44a5-80fd-f06ccd322635)

# Usage

Check IP by

```bash
ifconfig
```

If you got this:

![ifconfig](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-openssh-server-on-ubuntu-and-ssh-usage%2Fifconfig.png?alt=media&token=bb9e2554-3172-4f15-92e4-107d7edd14d6)

Install `ifconfig` by 

```bash
sudo apt install net-tools -y
```

Or use the command to get your IP address

```bash
ip addr
```

And connect via 

```bash
ssh <username>@<hostname> 
```

Or 

```bash
ssh <username>@<hostname> -p <port>
```

To using default 22 port to connect

![connect-host-via-ssh](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-openssh-server-on-ubuntu-and-ssh-usage%2Fconnect-host-via-ssh.png?alt=media&token=4f510762-7107-4e2c-871b-3925286c908c)

Enable ssh service start on boot：

```bash
sudo systemctl enable ssh
```

Let firewall allow ssh service

```bash
sudo ufw allow ssh
# or
sudo ufw allow 22
```

# Allow root login

```bash
sudo vim /etc/ssh/sshd_config
# change "PermitRootLogin no" to "PermitRootLogin yes"
```

# ssh keyless login

Create ssh rsa key on the computer you want to connect to host

```bash
[neil@yimincai.net ~]$ ssh-keygen -t rsa

Generating public/private rsa key pair.
Enter file in which to save the key (/home/neil/.ssh/id_rsa): [Press enter key]
Created directory '/home/neil/.ssh'.
Enter passphrase (empty for no passphrase): [Press enter key]
Enter same passphrase again: [Press enter key]
Your identification has been saved in /home/neil/.ssh/id_rsa.
Your public key has been saved in /home/neil/.ssh/id_rsa.pub.
The key fingerprint is:
1f:ad:49:00:4a:d5:ab:99:b3:b0:f9:09:91:c4:ed:d2 neil@yimincai.net
The key's randomart image is:
+--[ RSA 2048]----+
|        ..oooE.++|
|         o. o..  |
|          ..   . |
|         o  . . o|
|        S .  . + |
|       . .    . o|
|      . o o    ..|
|       + +       |
|        +.       |
+-----------------+
```

Create .ssh Directory on host server

```bash
[neil@yimincai.net ~]$ ssh alyssa@192.168.50.6 mkdir -p .ssh

The authenticity of host '192.168.50.6 (192.168.50.6)' can't be established.
RSA key fingerprint is 48:0e:28:11:d6:81:68:16:04:5f:db:49:02:la:12:4e.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.50.6' (ECDSA) to the list of known hosts.
alyssa@192.168.50.6's password: [Enter Your Password Here]
```

Copy public key from local to host server

```bash
cat ~/.ssh/id_rsa.pub | ssh alyssa@192.168.50.6 'cat >> .ssh/authorized_keys'
```

On host server restart ssh service

```bash
service ssh restatus
```

On host server check ssh service status

```bash
service ssh status
```

![ssh-status](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-openssh-server-on-ubuntu-and-ssh-usage%2Fssh-status.png?alt=media&token=eca58be5-7ebb-42ad-9e97-b6b7da906b17)