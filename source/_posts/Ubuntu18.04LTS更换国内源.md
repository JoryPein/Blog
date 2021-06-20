---
title: Ubuntu18.04 LTS 更换国内源
date: 2021-06-20 11:50
categories:
  - Ubuntu
tags:
  - Linux
  - Ubuntu
  - Debian
  - Network
  - Mirror
---
## 命令

### 国内Ubuntu源站点列表

- http://cn.archive.ubuntu.com/ubuntu/
- http://mirrors.huaweicloud.com/repository/ubuntu/
- http://mirrors.163.com/ubuntu/
- http://mirrors.sohu.com/ubuntu/
- http://mirrors.yun-idc.com/ubuntu/
- http://mirrors.ustc.edu.cn/ubuntu/

### 一键配置国内源

```shell
cp /etc/apt/sources.list /etc/apt/sources.list.bak
cat <<EOF > /etc/apt/sources.list
deb http://cn.archive.ubuntu.com/ubuntu/ bionic main restricted
deb http://cn.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb http://cn.archive.ubuntu.com/ubuntu/ bionic universe
deb http://cn.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb http://cn.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
EOF
cat /etc/apt/sources.list
```

### 切换国内镜像站点

``` shell
sudo sed -i 's/cn.archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
cat /etc/apt/sources.list
```

### 更新源

```shell
sudo apt update
```

## 参考

1.[USTC Open Source Software Mirror](http://mirrors.ustc.edu.cn/)