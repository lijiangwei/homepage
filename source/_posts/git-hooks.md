---
title: git hooks实现自动部署
date: 2018-05-03 10:24:56
tags:
    - git
    - hooks
categories:
    - git
---

# 使用git hooks实现远程仓库的本地部署
`git push`代码以后自动部署到本地的`web`服务器目录下。
修改仓库下面的`post-receive`文件
```
# --work-tree是设置工作目录
# --git-dir设置仓库的本地路径
# -f 强制执行
git --work-tree=/www/wwwroot/xxx/ --git-dir=/var/opt/gogs/gogs-repositories/lijiangwei/blog.git checkout -f
```

参考：[https://blog.csdn.net/zstack_org/article/details/53100257](https://blog.csdn.net/zstack_org/article/details/53100257)

