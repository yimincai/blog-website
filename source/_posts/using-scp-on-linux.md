---
title: Linux 從遠端伺服器複製檔案 - scp
id: using-scp-on-linux
author: Yi-Min Cai
mathjax: false
date: 2020-06-05 19:57:10
categories: Linux
tags:
    - Linux
    - Terminal
---
# 摘要

scp是一種Linux指令，可以實現跨Internet(WAN/LAN)傳送資料。
<!-- more -->

```bash
#example:
scp -r neil@192.168.50.6:/home/neil/Documents/Dev/ ~/Downloads
```

```bash
# -r 指複製整個目錄（資料夾）
scp -r <username>@host:<which remote dir cp to> <local dir>
```

![scp-usage](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fusing-scp-on-linux%2Fscp-usage.png?alt=media&token=4fddb05a-0e93-471c-ba0f-53b769e29b66)