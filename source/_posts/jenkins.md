---
title: jenkins
date: 2019-03-05 22:56:18
tags:
    - CI
    - jenkins
categories:
    - jenkins
---

# 安装

1. centos7系统安装

``` shell
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
yum install jenkins
```

> 官方安装比较慢，使用下面的国内地址

``` shell
wget https://mirrors.tuna.tsinghua.edu.cn/jenkins/redhat-stable/jenkins-2.150.3-1.1.noarch.rpm
rpm -ivh jenkins-2.150.3-1.1.noarch.rpm
```

# 配置

* 修改端口

```
vim /etc/sysconfig/jenkins
```

# 启动

``` shell
service jenkins start | stop | restart

# 设置开机启动
sudo chkconfig jenkins on
```
