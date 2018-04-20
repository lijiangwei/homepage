---
title: Hexo集成Travis CI
tags:
  - hexo
  - travis
categories:
  - 技术
abbrlink: e3c326c6
date: 2018-04-19 09:48:22
---

travis的配置和使用参考：[http://dmego.me/2017/10/13/deylpoy-hexo-with-TravisCI.html](http://dmego.me/2017/10/13/deylpoy-hexo-with-TravisCI.html)

# 增加同步推送到gitee
gitee也有令牌，但是gitee的令牌暂时不支持像github的token那样有推送代码的权限，gitee的推送有两种方式：
1. 通过https协议使用用户名、密码推送  `https://用户名:密码@gitee.com/用户/仓库名.git`
2. 通过ssh协议，使用私钥文件免密推送  `git @ gitee.com/用户/仓库名.git`

由于代码都是公开的，不能把密码和ssh私钥直接放到代码里，两种方式都需要通过trasiv提供的加密服务，对密码或者私钥文件进行加密。下面是加密和配置的流程：

## 登录trasiv命令行
trasiv命令行需要ruby环境，建议在linux环境操作，先安装ruby和ruby的gem。
```
# 安装travis命令行
gem install travis
```
在window环境操作一直报ssl证书错误（网上有解决办法，我没有试），我是在阿里云的服务器上完成的加密。

登录travis的命令行，中间会让输入github的用户名、密码登录travis
```
travis login #登录命令

We need your GitHub login to identify you.
This information will not be sent to Travis CI, only to api.github.com.
The password will not be displayed.

Try running with --github-token or --auto if you don't want to enter your password anyway.
# 使用github的用户名、密码登录
Username: xxx@xxx.xxx
Password for xxx@xxx.xxx: ***
Successfully logged in as demo!
```

## 加密密码
加密可以参考travis官网的文档[https://docs.travis-ci.com/user/encrypting-files/](https://docs.travis-ci.com/user/encrypting-files/)
如果密码中有特殊符号，需要转义：例如@需要转成%40

首先从github的仓库clone一份代码到本地，确保根目录有`.travis.yml`文件，下面的命令都是在代码的根目录操作的。
```
# gitee_password变量名，xxx是gitee的用户名密码
$ travis encrypt gitee_password=xxx --add
```
`.travis.yml`文件的`globar`会增加一个密文`secure`字段

修改`.travis.yml`文件，增加推送gitee的代码
```
# GE_REF和GH_REF一样是gitee要推送的仓库地址 gitee.com/用户/仓库名.git
after_script:
- cd ./public
- git init
- git config user.name "用户"
- git config user.email "xxx@xxx.com"
- git add .
- git commit -m "Update Blog By TravisCI With Build $TRAVIS_BUILD_NUMBER"
- git push --force --quiet "https://${GH_TOKEN}@${GH_REF}" master:master
- git push --force "https://用户:${gitee_password}@${GE_REF}" master:master
```
把修改后的`.travis.yml`文件推送到github服务器上就可以了。

## 加密ssh私钥文件
也需要先登录trasiv的命令行
公钥、私钥文件的生成和使用参考[gitee帮助文档](http://git.mydoc.io/?t=180845)

```
# 例如私钥文件是 ~/.ssh目录下的id_rsa
travis encrypt-file ~/.ssh/id_rsa --add
# 下面是命令行打印的日志
Detected repository as xxx/xxx, is this correct? |yes| yes
encrypting ~/.ssh/id_rsa for xxx/xxx
storing result as id_rsa.enc
storing secure env variables for decryption

Make sure to add id_rsa.enc to the git repository.
Make sure not to add ~/.ssh/id_rsa to the git repository.
Commit all changes to your .travis.yml.
```

`.travis.yml`文件会增加几行配置信息
```
before_install:
  - openssl aes-256-cbc -K $encrypted_d89376f3278d_key -iv $encrypted_d89376f3278d_iv
  -in id_rsa.enc -out ~\/.ssh/id_rsa -d
```
同时根目录会增加一个加密后的文件`id_rsa.enc`

`.travis.yml`文件增加推送到gitee的代码
```
# GE_REF的配置是 gitee.com:用户名/仓库名.git
after_script:
- cd ./public
- git init
- git config user.name "用户"
- git config user.email "xxx@xxx.com"
- git add .
- git commit -m "Update Blog By TravisCI With Build $TRAVIS_BUILD_NUMBER"
- git push --force --quiet "https://${GH_TOKEN}@${GH_REF}" master:master
- git push --force "git@${GE_REF}" master:master
```

把修改后的`.travis.yml`文件和新增的`id_rsa.enc`文件推送到服务器。

这个我测试的时候报错
```
$ openssl aes-256-cbc -K $encrypted_cdd288e44784_key -iv $encrypted_cdd288e44784_iv -in id_rsa.enc -out ~\/.ssh/id_rsa -d
~/.ssh/id_rsa: No such file or directory
```
这种方式应该是可行的，目前暂时没有时间研究这个问题，后续再解决。

参考：
[https://www.cnblogs.com/dmego/p/7664877.html](https://www.cnblogs.com/dmego/p/7664877.html)
[http://notes.iissnan.com/2016/publishing-github-pages-with-travis-ci/](http://notes.iissnan.com/2016/publishing-github-pages-with-travis-ci/)
[https://segmentfault.com/a/1190000011218410](https://segmentfault.com/a/1190000011218410)