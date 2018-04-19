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

# 工作原理
博客的源代码在`github`的homepage仓库的`master`分支，个人主页在`xxx.github.io`仓库的`master`分支，`push`源代码到homepage仓库以后，通过travis执行`hexo g`命令编译出静态文件然后推送到`xxx.github.io`仓库。整个工作流程是：

* 更新代码到 Github 的 homepage 仓库
* Github 告诉 Travis CI说有个东西变了
* Travis CI 立马安排 Build
* Travis CI build 成功后，将输出丢到 xxx.github.io 仓库

# 配置流程

## 生成 Access Token
`Travis CI`构建后的代码要推送到`xxx.github.io`仓库，有用户名、密码才能向远程仓库推送代码，还有一种方式是通过token授权代替用户名、密码向远程仓库推送代码。

参考：
[https://www.cnblogs.com/dmego/p/7664877.html](https://www.cnblogs.com/dmego/p/7664877.html)
[http://notes.iissnan.com/2016/publishing-github-pages-with-travis-ci/](http://notes.iissnan.com/2016/publishing-github-pages-with-travis-ci/)