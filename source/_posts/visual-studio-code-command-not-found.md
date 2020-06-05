---
title: 'Visual Studio code : code command not found'
id: Visual-Studio-code-code-command-not-found
author: Yi-Min Cai
date: 2020-05-28 01:51:18
categories: Visual Studio Code
tags: 
    - Visual Studio Code
    - Terminal
mathjax: false
---
# 摘要

在Terminal中使用VScode中自帶的code函數時，出現錯誤如下：

```bash
command not found code
```

<!-- more -->

{% asset_img code-command-not-found.png %}

# 除錯

1. 確保已將Visual Studio Code應用程式放到Applications文件夾中，否則 VS code 重新啟動後，您將不得不再次執行此過程
2. 接下來打開Visual Studio Code，透過**（⇧⌘P）**打開面板然後輸入以找到Shell命令：`shell command`

選擇 **Install 'code' command in PATH**


{% asset_img vscode-shell-command.png %}

最後重啟Terminal或執行(`~/.bash_profile`, `~/.zshrc`, `~/.profile`, or `~/.bashrc`)：

```bash
$ source ~/.zshrc
```

# 參考資料

- [Visual Studio Code Documentation](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)