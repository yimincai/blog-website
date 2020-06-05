---
title: Install ESXi VMware-tools on Linux
id: install-esxi-vmware-tools-on-linux
author: Yi-Min Cai
mathjax: false
date: 2020-06-05 20:05:23
categories: ESXi
tags:
    - ESXi
    - Linux
    - Ubuntu
---
# Install ESXi vmware-tools on Linux

Visit vCenter web page choose the VM, click `Install VMware-tools` and MOUNT.

<!-- more -->

![mount-vmware-tools-cd](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-esxi-vmware-tools-on-linux%2Fmount-vmware-tools-cd.png?alt=media&token=4678933e-d0bc-4591-b13e-ce45ac59c87b)

Back to VM double click VMware Tools on desktop

![click-dvd-on-desktop](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-esxi-vmware-tools-on-linux%2Fclick-dvd-on-desktop.png?alt=media&token=80d2bb24-d3da-4c1d-9c56-377e0100221b)

And double click `VMwareTools-<version>.tar.gz`

![click-tar-gz-file](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-esxi-vmware-tools-on-linux%2Fclick-tar-gz-file.png?alt=media&token=a2cd2bf8-4981-48ad-906d-c918fd60edd2)

Extract it on `~/Desktop`

![extract-to-desktop](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-esxi-vmware-tools-on-linux%2Fextract-to-desktop.png?alt=media&token=2417f7ef-8a29-49c9-8a3c-8aae1c111939)

In the dir right click and choose `Open in Terminal`

![open-dir-in-terminal](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-esxi-vmware-tools-on-linux%2Fopen-dir-in-terminal.png?alt=media&token=ba0a4b82-0698-447d-b0b3-fe00539bf8b1)

Change file permission to install it

```bash
sudo chmod u+x vmware-install.pl
```

![change-install-file-permission](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-esxi-vmware-tools-on-linux%2Fchange-install-file-permission.png?alt=media&token=cfa302ca-5fa3-4f02-8fee-042b3832e9d5)

Install it

```bash
sudo ./vmware-install.pl
```

Just type `yes` and press `Enter` to the end of installation, enjoy

![done-enjoy](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-esxi-vmware-tools-on-linux%2Fdone-enjoy.png?alt=media&token=cdfb5470-0691-4b44-8da8-eb5488e4fec6)

# 參考資料

- [VMware Workstation 5.0](https://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html)