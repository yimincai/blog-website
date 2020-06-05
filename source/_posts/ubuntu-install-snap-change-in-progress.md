---
title: 解決Ubuntu安裝軟體snap "code-insiders" has "install-snap" change 
id: ubuntu-install-snap-change-in-progress
author: Yi-Min Cai
mathjax: false
date: 2020-06-05 17:40:24
categories: Linux
tags:
    - Ubuntu
    - Visual Studio Code
    - Linux
---
# 摘要
:warning: 我通過Ubuntu自帶的『Software』下載安裝，可是他卻提示我：

 ```bash
 Unable to install "Visual Studio Code": snap "code" has "install-snap" change in progress.
 ```
<!-- more -->

![install-snap-change-in-progress](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fubuntu-install-snap-change-in-progress%2Finstall-snap-change-in-progress.png?alt=media&token=de46b63d-9865-4cbb-a91e-a0b99beff59d)

## 原因：

軟體之前安裝過一次，但是因為一些原因沒有安裝成功

## 解決方法：

查看安裝情況：

```bash
snap changes
```

![snap-changes](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fubuntu-install-snap-change-in-progress%2Fsnap-changes.png?alt=media&token=d042e40c-c521-4369-b134-a8b690eaf9e7)

終止，並重新安裝

```bash
sudo snap abort 3
```

![snap-abort](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fubuntu-install-snap-change-in-progress%2Fsnap-abort.png?alt=media&token=edcc8541-453b-448e-9c88-6d1db37a637a)

就好了！