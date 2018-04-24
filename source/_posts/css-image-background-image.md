---
title: CSS边框问题
date: 2018-04-23 21:30:52
tags:
    - css
    - html
categories:
    - html
---

最近开发一个页面使用background-image属性作为img标签的背景，img没有设置src属性，图片一直显示一个边框，怎么也去不掉。
***示例***
![](http://p7dkryqvb.bkt.clouddn.com/css_border_bug.png)

# 解决办法
后来在网上找到解决方法，图片没有设置src属性，浏览器会当作没有图片处理，会默认给一个边框，解决版本是给图片src一个空白的图片。
这种情况最好不要使用img标签，更换为其他标签。
