---
title: Ubuntu网络疑难问题解决方案
date: 2021-06-14 06:28
categories: Snippet
tags:
  - Linux
  - Ubuntu
  - Network
  - Snippet
---
## 疑难问题解决方案

### 0x00.Ubuntu网卡图标丢失，无法联网

在命令行中输入下面的代码，并回车执行

``` bash
sudo /etc/init.d/network-manager stop && 
sudo rm -rf /var/lib/NetworkManager/NetworkManager.state && 
sudo sed -i 's/managed=false/managed=true/g' /etc/NetworkManager/NetworkManager.conf && 
sudo /etc/init.d/network-manager start
```

