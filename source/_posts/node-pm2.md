---
title: pm2使用笔记
date: 2018-05-02 17:02:07
tags:
    - node
    - pm2
categories:
    - node
---

# 简介
> pm2=P(rocess) M(anager)2，是可以用于生产环境的Nodejs的进程管理工具，并且它内置一个负载均衡。它不仅可以保证服务不会中断一直在线，并且提供0秒reload功能，还有其他一系列进程管理、监控功能。并且使用起来非常简单。

# 安装
```
npm install -g pm2
```

# 使用

## 启动项目
```
pm2 start app.js
```

## 显示所有进程状态
```
pm2 list
```

## 监视所有进程
```
pm2 monit
```

## 显示所有进程日志
```
pm2 logs 
```

## 停止所有进程
```
pm2 stop all
```

## 重启所有进程
```
pm2 restart all
```

## 停止指定的进程
```
pm2 stop 0 
```

## 重启指定的进程
```
pm2 restart 0
```

## 杀死全部进程
```
pm2 delete all 
```

## 杀死指定的进程
```
pm2 delete 0
```

## 启动程序增加参数
--后面增加参数
```
pm2 start http-server -- -p 8080 -d false
```