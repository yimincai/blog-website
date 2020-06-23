---
title: Machine Learning Ubuntu 18.04 環境建置手札
id: building-machine-learning-env-on-ubuntu18.04
author: Yi-Min Cai
mathjax: false
date: 2020-06-05 19:50:07
categories: Machine Learning
tags:
    - Linux
    - Ubuntu
    - Machine Learning
    - Openssh server
    - Python venv
    - Conda venv
---
# 重新安裝ssh server

```bash
sudo apt-get remove openssh-server
sudo reboot
sudo apt-get install openssh-server
```
<!-- more -->

# ssh允許使用root登入

```bash
sudo vim /etc/ssh/sshd_config
# change "PermitRootLogin no" to "PermitRootLogin yes"
```

# ssh免密碼登入

建立ssh rsa key

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

Copy public key to host server

```bash
cat ~/.ssh/id_rsa.pub | ssh alyssa@192.168.50.6 'cat >> .ssh/authorized_keys'
```

 重新啟動ssh服務

```bash
service ssh restatus
```

確認ssh服務狀況

```bash
service ssh status
```

防火牆設定允許ssh服務

```bash
sudo ufw allow ssh
# or
sudo ufw allow 22
```

# 設定Python環境

## 1. 使用Python3

```bash
sudo apt-get install python3-venv
```

## 建立Python3虛擬環境

```bash
# 在當前資料夾建立環境
python3 -m venv <venvName>
```

啟動環境

```bash
source ./<venvName>/bin/activate
```

## 2. 使用Conda作為Python環境

## (Option)移除Python 3.6

:warning: 不要輕易移除，曾試過移除後GUI失效

```bash
sudo apt-get remove python3.6
```

移除Python 3.4及其dependent

```bash
sudo apt-get remove --auto-remove python3.6
```

清除Python 3.4

```bash
sudo apt-get purge python3.4
# or
sudo apt-get purge --auto-remove python3.6
```

## 安裝 Conda for Python 3.7 64bit

可以到Conda Docs頁面確認下載版本或使用下方範例(Python 3.7)

```bash
cd ~/Download
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

![wget-miniconda](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fbuilding-machine-learning-env-on-ubuntu18.04%2Fwget-miniconda.png?alt=media&token=8b77e846-19c2-4813-803c-eee00ad197ac)

更改檔案權限

```bash
sudo chmod +x ./Miniconda3-latest-Linux-x86_64.sh
```

安裝

```bash
./Miniconda3-latest-Linux-x86_64.sh
```

![install-miniconda](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fbuilding-machine-learning-env-on-ubuntu18.04%2Finstall-miniconda.png?alt=media&token=40d7b72f-0cb6-4495-bdf6-02117d85cd62)

同意license terms

![agree-license-terms](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fbuilding-machine-learning-env-on-ubuntu18.04%2Fagree-license-terms.png?alt=media&token=6d4ad8ea-92b8-4ec6-a087-9f3afa7294c3)

Hit Enter

![conti-install-conda](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fbuilding-machine-learning-env-on-ubuntu18.04%2Fconti-install-conda.png?alt=media&token=8520e198-43a6-434d-b497-a36cfc50da21)

Type "yes"

![run-conda-init](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fbuilding-machine-learning-env-on-ubuntu18.04%2Frun-conda-init.png?alt=media&token=52afa2c7-4936-4d7f-a7f7-7f6c22e52146)

重啟Terminal、測試command

```bash
conda info
```

![conda-info](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fbuilding-machine-learning-env-on-ubuntu18.04%2Fconda-info.png?alt=media&token=6a57f8d9-f8c9-4e23-b6ff-5f51671bf814)

# 建立Conda venv（虛擬環境）

確認安裝了多少個虛擬環境

```bash
conda env list
```

假設建一個名為 `ml`  的 venv 並設定Python 為3.6

```bash
conda create --name ml python=3.6
```

Press `y`

![create-venv-y](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fbuilding-machine-learning-env-on-ubuntu18.04%2Fcreate-venv-y.png?alt=media&token=38b2dd0f-f86e-4fee-b45e-9bcbd939323a)

```bash
# To activate this environment, use
conda activate ml
# To deactivate an active environment, use
conda deactivate
```

刪除虛擬環境或package

```bash
conda remove --name ml numpy
```

刪除虛擬環境

```bash
conda env remove --name myenv
```

# 安裝 Machine Learning 相關環境

安裝常用環境，可參考下方文章

- [Tensorflow與Keras版本對應](https://yimincai.net/2020/tensorflow-corresponding-to-keras-version)

```bash
pip install numpy
pip install pandas
pip install scikit-learn
pip install --upgrade tensorflow
pip install Keras
pip install Pillow
pip install tensorflow
pip install torch
.
.
.
etc.
```

⚠ 若在 `import tensorflow as tf` 時出現： `Illegal instruction (core dumped)`經確認是CPU缺少avx指令集的關係（CPU架構太舊不支援）。

可降低Tensorflow版本解決

```bash
pip uninstall tensorflow
# and then
pip install tensorflow==1.4
```

<!-- <mark>Continue .. </mark> -->
