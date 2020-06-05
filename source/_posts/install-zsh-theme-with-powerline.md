---
title: 安裝zsh主題powerline
id : install-zsh-theme-with-powerline
author: Yi-Min Cai
date: 2020-05-27 18:25:04
categories: Terminal
tags:
    - macOS
    - zsh
mathjax: false
---

# 成果
<!-- {% asset_img powerline-theme.png %} -->
![powerline-theme](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-zsh-theme-with-powerline%2Fpowerline-theme.png?alt=media&token=4c9773da-3cf3-4678-8a6b-df61749f6602)

<!-- more -->

# zsh settings

Edit .zshrc
```bash
vim ~/.zshrc
```
Download theme
```bash
git clone https://github.com/jeremyFreeAgent/oh-my-zsh-powerline-theme.git
```
Go to dir
```bash
cd ./oh-my-zsh-powerline-theme
```

Install theme
```bash
./install_in_omz.sh
```
Theme conf in file ".zshrc"
```bash
ZSH_THEME="powerline"
POWERLINE_HIDE_HOST_NAME="true"
POWERLINE_DISABLE_RPOMPT="true"
POWERLINE_FULL_CURRENT_PATH="true"
POWERLINE_PATH="short"
```
Install zsh-completions
```bash
brew install zsh-completions
```
Install zsh-autosuggestions
```bash
brew install zsh-autosuggestions
```
Install zsh-syntax-highlighting
```bash
brew install zsh-syntax-highlighting
```
zsh plugin setting in file ".zshrc" at /home/{username}
```bash
source /usr/local/share/zsh-autosuggestions/zsh-autosuggestions.zsh
```

```bash
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

zsh-completions settings

```bash
fpath=(/usr/local/share/zsh-completions $fpath)
```
Download powerline fonts
```bash
git clone https://github.com/powerline/fonts.git
```
Go to dir
```bash
cd fonts/
```
Install fonts
```bash
./install.sh
```
delete fonts installation files
```bash
cd ..
```
```bash
rm -rf fonts
```



# iTerm2 settings

- Change font to 14pt "Fira Mono Medium for Powerline"

- Let iTerm2 colorset be "Brogrammer"