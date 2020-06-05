---
title: Ubuntu Change Screen Resolution through the Terminal
id: ubuntu-change-screen-resolution-through-the-terminal
author: Yi-Min Cai
mathjax: false
date: 2020-06-05 19:28:55
categories: Linux
tags:
    - Ubuntu
    - Linux
    - Terminal
---
# 摘要

Xrandr工具可用於動態設定螢幕輸出解析度及比例，默認情況下，此軟體安裝在Ubuntu 18.04上。

<!-- more -->

# Changing Screen Resolution through Terminal
![terminal](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fubuntu-change-screen-resolution-through-the-terminal%2Fterminal.png?alt=media&token=03383e5f-75c6-4f82-961e-a1521c47dc3b)


我們使用xrandr工具調整螢幕尺寸：

```
-s, –size size-index or –size <寬>x<高>
```

```bash
xrandr–size [size-index]
```

For example:

```bash
xrandr --size:3
```

![xrandr4x3](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fubuntu-change-screen-resolution-through-the-terminal%2Fxrandr4x3.png?alt=media&token=e22b95ed-0ccb-4a82-87d8-5438096d3c1e)

Or,

```bash
xrandr–size [widthxheight]
```

For example:

```bash
xrandr --size 1280x800
```

![xrandr1280x800](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Fubuntu-change-screen-resolution-through-the-terminal%2Fxrandr1280x800.png?alt=media&token=cf884533-aaff-44fa-9a57-ce3cab074002)

通過這個簡單的工具我們可以在 command line 中調整畫面解析度、比例。

# 參考資料

- [How to Change Screen Resolution through the Ubuntu Terminal](https://vitux.com/how-to-change-screen-resolution-through-the-ubuntu-terminal/)
