---
title: Hexo集成Travis CI
date: 2018-04-19 09:48:22
tags:
    - hexo
    - travis
categories: 
  - 技术
---

# 背景
最近在使用`hexo`搭建个人博客，每次发表一篇文章，要使用`hexo g -d`命令生成静态网页并推送到`GitHub`远程仓库,还要把hexo的源码推送到`GitHub`的另一个分支。现在通过`Travis CI`就能自动构建自己的博客，我们只需将博客的源码`push`到`hexo源文件`分支即可。

# Travis CI 介绍
>Travis CI 是目前新兴的开源持续集成构建项目，它与`jenkins，GO`的很明显的特别在于采用`yaml`格式，简洁清新独树一帜。目前大多数的 github 项目都已经移入到 Travis CI 的构建队列中。

参考：
[https://www.cnblogs.com/dmego/p/7664877.html](https://www.cnblogs.com/dmego/p/7664877.html)
[http://notes.iissnan.com/2016/publishing-github-pages-with-travis-ci/](http://notes.iissnan.com/2016/publishing-github-pages-with-travis-ci/)