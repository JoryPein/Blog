---
title: 在Ubuntu下安装SublimeText
date: 2021-06-18 09:30
categories: 
  - Ubuntu
tags:
  - Linux
  - Ubuntu
  - Editor
  - apt
---

## 安装

```shell
# 安装GPG key
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -

# 增加apt对https源的支持
sudo apt-get install apt-transport-https

# 增加稳定版的sublimetext源
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list

# 更新apt源
sudo apt-get update

# 安装Sublime Text
sudo apt-get install sublime-text

# 建立软链接
ln -s /opt/sublime_text/sublime_text /bin/subl
```

## 参考

1. [Linux Package Manager Repositories – Sublime Text Documentation](https://www.sublimetext.com/docs/linux_repositories.html)
