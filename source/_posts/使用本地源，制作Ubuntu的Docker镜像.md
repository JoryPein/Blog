---
title: 使用本地源，制作Ubuntu的Docker镜像
date: 2021-06-20 12:00
categories:
  - Docker
tags:
  - Linux
  - Ubuntu
  - Debian
  - Docker
  - Mirror
---

## 步骤

创建名为ubuntu1804u的dockerfile文件

```dockerfile
FROM ubuntu:18.04
ADD sources.list /etc/apt/
RUN apt update
```


执行命令
```shell
cp /etc/apt/sources.list sources.list
docker build -f ubuntu1804u -t ubuntu:18.04u .
rm -f sources.list
```

查看docker镜像

```shell
docker images
```

