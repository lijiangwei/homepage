---
title: git常用总结
date: 2018-06-15 22:59:38
tags:
    - git
category:
    - git
---

# 配置

## 记录用户名、密码
```
git config --global credential.helper store
```

## 设置代理
```
git config --global http.proxy http://127.0.0.1:808
git config --global https.proxy https://127.0.0.1:808
```

## 拉取远程仓库分支
```
git pull <远程库名> <远程分支名>:<本地分支名> 
```