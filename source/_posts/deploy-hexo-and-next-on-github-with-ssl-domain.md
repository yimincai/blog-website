---
title: 部署Hexo+Next於Github-Page+ssl憑證+自定義Domain
id: deploy-hexo-and-next-on-github-with-ssl-domain
author: Yi-Min Cai
mathjax: false
date: 2020-05-28 02:39:12
categories: Hexo
tags:
    - Web
    - SSL
    - Hexo
    - custom domain
    - Github page
    - next
---
# 摘要

Hexo 是一款靜態網頁產生器，它是基於 Node.js 的快速且簡單的網頁框架被許多 Bloger 使用，因為是靜態網頁，它沒有我們常見的資料庫等後端系統，Blog 常用的留言板等功能則透過 third-party plugin 解決。

<!-- more -->

# 環境需求

- 安裝 [Node.js](https://nodejs.org/en/)
- 安裝 [Git](https://git-scm.com/)

# 安裝Hexo

```bash
npm install -g hexo-cli
```

{% asset_img install-hexo-cli.png %}

# 使用 Hexo

安裝完Hexo 後需要在指定資料夾 `<dir>`  中新建所需要的的檔案。

```bash
# 建立 Project 資料夾
$ mkdir <dir-name>
# 資料夾初始化
$ hexo init <dir>
$ cd <dir>
# 安裝
$ npm install
```

{% asset_img hexo-init.png %}

Project tree：

{% asset_img hexo-project-tree.png %}

<mark>Continue ..</mark>