---
layout: post
title: Ubuntu Apt Sources
categories: [Linux]
description: 
keywords: Ubuntu,Apt
typora-root-url: ..\..
---
Ubuntu 18.04 国内源

# 简述

1、备份`/etc/apt/sources.list`

```shell
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

2、编辑`/etc/apt/sources.list`，添加以下一种国内源即可

```shell
sudo vim /etc/apt/sources.list
```

3、更新源

```shell
sudo apt-get update
```




# 阿里源

```shell
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
# deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
# deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
# deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
# deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
```

# 163源

```shell
deb http://mirrors.163.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://mirrors.163.com/ubuntu/ bionic main restricted universe multiverse
# deb-src http://mirrors.163.com/ubuntu/ bionic-security main restricted universe multiverse
# deb-src http://mirrors.163.com/ubuntu/ bionic-updates main restricted universe multiverse
# deb-src http://mirrors.163.com/ubuntu/ bionic-proposed main restricted universe multiverse
# deb-src http://mirrors.163.com/ubuntu/ bionic-backports main restricted universe multiverse
```

# 清华源

```shell
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
```

# 中科大源

```shell
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
# deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
# deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
# deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
# deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
```

