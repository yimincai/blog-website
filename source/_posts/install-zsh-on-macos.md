---
title: 在macOS安裝ZSH
id: install-zsh-on-macos
author: Yi-Min Cai
date: 2020-05-27 17:16:10
categories:
    - Terminal
tags:
    - macOS
    - zsh
    - oh-my-zsh
mathjax: false
---
# 安裝概覽:
1. Install Homebrew
2. Install zsh
3. Switch default shell to zsh
4. Install oh-my-zsh
5. Edit setting

<!-- more -->

# 安裝Homebrew
Install [Homebrew](https://brew.sh/index_zh-tw "Homebrew")
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

# 安裝zsh
```bash
brew install zsh
```

Confirm the installation
```bash
zsh --version
```

# 切換預設shell至zsh

```bash
sudo sh -c "echo $(which zsh) >> /etc/shells"
```

```bash
chsh -s $(which zsh)
```

Restart termianl

```bash
echo $SHELL
```

if success you'll see:
```bash
/usr/local/bin/zsh
```

# 安裝oh-my-zsh
```bash
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
```
Copy oh-my-zsh templete to zshrc
```bash
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```
DONE!