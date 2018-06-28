---
title: eclipse打开npm依赖包卡死
date: 2018-06-28 09:00:46
tags:
    - eclipse
    - npm
categories:
    - 工具
    - eclipse
---

前端工程安装了很多npm的包，使用eclipse开发时导致eclipse经常卡死的解决办法：

1. 把node_modules目录过滤掉
2. 把node_modules从svn版本控制中忽略掉

# 过滤node_modules目录
右键单击工程，选择Properties->Resourse->Resource Filters，点击Add按钮添加要过滤的目录
![](http://qiniu.xiaosl.cn/resource_filter.png)

# svn忽略node_modules目录
右键单击工程，选择Term->设置属性
![](http://qiniu.xiaosl.cn/eclipse_svn_ignore.png)

属性名选择svn:ignore，内容输入node_modules
![](http://qiniu.xiaosl.cn/eclipse_svn_property.png)
