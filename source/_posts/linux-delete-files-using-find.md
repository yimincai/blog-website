---
title: Linux使用find指令查詢特定檔案及目錄並刪除
id: linux-find-specific-folder-or-file-and-delete
author: Yi-Min Cai
mathjax: false
date: 2020-05-28 17:05:51
categories: Linux
tags:
	- Linux
	- macOS
	- Terminal
---
# 摘要

在Linux底下當我們要針對資料夾的特定檔案執行操作時，如果一個一個的做非常麻煩又沒消率，我們可以透過 `find` 指令解決這個問題，以下提供一個刪除檔案的例子。

<!-- more -->

# 命令格式

使用 `find` 命令將當前目錄下所有包含特定字元檔名的文件刪除：

```bash
find <路徑>  -name "<檔案名稱>" -exec <操作> {} \;
```

這邊有一個刪除操作的例子：

```bash
find .  -name "fileName.subName" -exec rm -rf {} \;
```

- `find .` ：表示尋找當前目錄
- `<檔案名稱>` 可以替換成： `*.git` 、 `*.git*` 、 `*subName*.*` ， `*` 為萬用字元
- `-exec` ：操作選項
- `rm -rf` ：強制刪除檔案及目錄
- `{} \;` ：固定寫法

# 常用指令

`-iname` ：搜尋名稱不區分大小寫

```bash
find /etc -iname 'hosts'
```

`-type f` ：搜尋**檔案**名稱

```bash
find /var/log -iname '*.txt' -type f
```

`-type d` ：搜尋**目錄**名稱

```bash
find /etc -iname 'tomcat' -type d
```

`-size +100M` ：搜尋 `/var` 下檔案大於100MB的檔案

```bash
find /var -type f -size +100M
```

`-size -100M` ：搜尋 `/var` 下檔案小於100MB的檔案

```bash
find /var -type f -size -100M
```

`-atime -14` ：檔案的最後讀取或執行時間到find 的執行時間差(access time)，以天為單位，本案例為十四天

```bash
find $HOME -type f -atime -14
```

`-amin -10` ：同 `-atime` ，改以分鐘為單位，本案例為三十分鐘

```bash
find $HOME -type f -amin -30
```

`-ctime +7` ：檔案的建立時間到find 的執行時間差(create time)，以天為單位，本案例為七天

```bash
find $HOME -type f -ctime +7
```

`-user <user name>` ：搜尋特定使用者檔案，本案例以 `neil` 為例

```bash
find $HOME -type f -user neil
```

`-0` ：同時找兩種檔名樣式的檔案(or)

```bash
find $HOME -name '*.dog' -o -name '*.cat'
```

`-and` ：同時找兩種檔名樣式的檔案(and)

```bash
find $HOME -name '*.dog' -o -name '*.cat'
```

# 其他指令

- d：目錄(directory)

- c：字型裝置檔案(character)

- b：區塊裝置檔案(block special)

- p：pipe (FIFO)

- f：一般檔案(regular file)

- l：symbolic link

- s：socket