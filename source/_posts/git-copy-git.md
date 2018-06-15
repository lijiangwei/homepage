---
title: 拷贝.git目录
date: 2018-06-15 22:41:33
tags:
    - git
categoriy:
    - git
---

> 有时候我们需要从远程仓库把代码下载到一个已经存在的目录，git clone的时候会报错，可以先把版本信息下载到一个空目录然后复制到当前目录，然后恢复到最新版本，这样当前目录就会包含版本信息。

```
#当前在workspace目录
git clone --no-checkout 远程仓库地址 tmp
mv tmp/.git ./
rm -rf tmp
git reset --hard HEAD
```

> 由于window、mac、linux系统的换行符不一样，导致mac系统下载下来的代码，git status的时候显示很多文件有修改，可以修改mac系统换行符的设置
```
git config --global core.autocrlf false
```
