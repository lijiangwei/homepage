---
title: Hexo集成Travis CI
date: 2018-04-19 09:48:22
tags:
    - hexo
    - travis
categories: 
  - 技术
---

参考：[http://dmego.me/2017/10/13/deylpoy-hexo-with-TravisCI.html](http://dmego.me/2017/10/13/deylpoy-hexo-with-TravisCI.html)

# 扩展
代码同步推送到gitee的pages服务。
```
## .travis.yml配置文件增加推送到gitee的代码
- git push --force --quiet "https://user:${GE_TOKEN}@${GE_REF}" master:master

## env.global增加配置
- GE_REF: gitee.com/user/reponame.git
```

travis配置gitee的令牌参数GE_TOKEN

参考：
[https://www.cnblogs.com/dmego/p/7664877.html](https://www.cnblogs.com/dmego/p/7664877.html)
[http://notes.iissnan.com/2016/publishing-github-pages-with-travis-ci/](http://notes.iissnan.com/2016/publishing-github-pages-with-travis-ci/)