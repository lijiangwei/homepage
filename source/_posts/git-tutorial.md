---
title: git常用总结
date: 2018-06-15 22:59:38
tags:
    - git
category:
    - git
---

# 配置

## 配置文件

> 配置文件有三个级别 仓库>全局>系统

1. 仓库配置
仓库级别配置文件在.git目录

查看仓库级别的配置
```
git config --local -l
```

2. 全局配置
全局配置文件在用户目录下，.gitconfig文件

查看全局配置项
```
git config --global -l
```

3. 系统配置
系统级别的配置在git的安装目录

## 记录用户名、密码

```
git config --global credential.helper store

# 修改用户名密码
git config --global credential.helper username
```

## 设置代理

```
git config --global http.proxy http://127.0.0.1:808
git config --global https.proxy https://127.0.0.1:808
```

## 删除配置

```
git config --unset xxx
```

## 拉取远程仓库分支

```
git pull <远程库名> <远程分支名>:<本地分支名> 
```

# 问题处理

## warning: http.proxy has multiple values

```
git config --unset-all http.proxy
```