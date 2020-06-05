---
title: macOS安裝與移除NVM
id: install-and-uninstall-nvm-on-macos
author: Yi-Min Cai
date: 2020-05-28 02:30:07
categories: Node.js
tags:
    - NVM
    - Node.js
    - macOS
mathjax: false
---

# 摘要

NVM（Node Version Manager），是一款Node.js的管理套件，可以透過NVM管理不同的Node.js版本，也可以隨時切換到其它版本。

<!-- more -->

# 安裝NVM

NVM官方建議直接使用cURL安裝或更新 `nvm`，雖說在macOS環境下一般都建議使用Homebrew來安裝，但安裝完後會有許多坑，因此我們就照官方建議來做吧！

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```

結果如下：

{% asset_img install-nvm.png %}

上面指令會將 `nvm` 的repository複製到 `~/.nvm` ，然後把source line加進你的 profile ( `~/.bash_profile` , `~/.zshrc` , `~/.profile` , or `~/.bashrc` )，之中；以我的例子會寫到 `~/.zshrc` 中，我們可以使用 `vim` 打開來看看：

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash
```

{% asset_img nvm-zshrc.png %}

完成以後，我們重新載入 `~/.zshrc` 看看 `nvm` 這個指令能不能用，顯示如下圖就代表安裝完成啦！

```bash
nvm --verison
```

{% asset_img nvm-version.png %}

# NVM 指令

查看有哪些 Node.js 版本可以安裝：

```bash
nvm ls-remote
```

{% asset_img nvm-ls-remote.png %}

也可以帶入<version>參數篩選：

{% asset_img ./nvm-ls-remote-13.png %}

列出本機安裝的資訊，可以看到我們都還沒安裝：

```bash
nvm ls
```

{% asset_img nvm-ls.png %}

# 安裝需要的 Node.js 版本

安裝 13.13.0
```bash
nvm install 13.13.0
```
使用 13.13.0
```bash
nvm use 13.13.0
```

這樣就會安裝並使用 `13.13.0` 的 Node.js。

{% asset_img nvm-install-13-13-0.png %}

# 設定預設Node.js版本

經過上面的設定後每次重新開啟Terminal，Node.js的設定還是會被重置，因此需要設定預設使用版本：

```bash
nvm alias default 13.13.0
```

{% asset_img nvm-alias-default.png %}

之後每次開啟都會使用 `13.13.0`

# NVM 指令整理

- `nvm --version` ：檢查 `nvm` 是否安裝成功，如果是會輸出版本號
- `nvm ls-remote` ：查看目前可安裝版本
- `nvm ls-remote <version> `：篩選版本號
- `nvm install <version>` ：安裝指定版本
- `nvm ls` ：查看本機目前安裝的版本
- `nvm use <version>` ：切換版本，但重啟Terminal會重置設定
- `nvm alias default <version>` ：設定每次開啟Terminal使用的Node.js版本
- `nvm -h ` ：列出所有指令選項

# 移除透過cURL安裝的NVM

刪除相關目錄：

```bash
rm -rf ~/.nvm
```
```bash
rm -rf ~/.npm
```
```bash
rm -rf ~/.bower
```

移除`~/.zshrc`內的`nvm`設定：

```bash
vim ~/.zshrc
```
刪除以下內容：
```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash
```

重啟 terminal，查詢以下指令，應該都沒有東西了：

```bash
nvm
```
```bash
node
```
```bash
npm
```


# 移除透過Homebrew安裝的NVM

```bash
brew uninstall node
```

一般來說Homebrew 的 `node` 套件會預設裝在 `/usr/local/bin` ，移除以下目錄：

```bash
rm -rf /usr/local/bin/node
```

```bash
rm -rf /usr/local/bin/npm
```

```bash
rm -rf /usr/local/bin/node_modules
```



確認是否完整移除：

```bash
which node
```



# 參考資料

- [Node.js](https://nodejs.org/en/)
- [NVM GitHub](https://github.com/creationix/nvm)
- [Node.js 環境設定-for mac](https://medium.com/@toumasaya/node-js-環境設定-for-mac-a2628836feaf)


