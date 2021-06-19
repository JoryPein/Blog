---
title: Ubuntu网卡图标丢失，无法联网
date: 2021-06-14 06:28
categories:
  - Ubuntu
tags:
  - Linux
  - Ubuntu
  - Network
  - Snippet
---
## 解决方法

在命令行中输入下面的代码，并回车执行

``` shell
sudo /etc/init.d/network-manager stop && 
sudo rm -rf /var/lib/NetworkManager/NetworkManager.state && 
sudo sed -i 's/managed=false/managed=true/g' /etc/NetworkManager/NetworkManager.conf && 
sudo /etc/init.d/network-manager start
```

