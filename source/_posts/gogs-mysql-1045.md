---
title: gogs访问数据库1045错误
date: 2018-05-09 11:23:55
tags:
    - gogs
    - 1045
categories:
    - git
---

gogs有时候会出现访问数据库没有权限的问题。
错误日志 
```
Error 1045: Access denied for user 'gogs'@'localhost' (using password: YES)
```

临时解决办法：给用户重新赋一下权限。