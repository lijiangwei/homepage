---
title: nginx常用配置
date: 2018-07-25 09:16:09
tags:
    - nginx
    - tutorial
categories:
    - nginx
---

# nginx 教程

## 隐藏html文件后缀
```
# 文件不存在时访问.html文件
location / {
    if (!-e $request_filename) {
        rewrite ^(.*)$ /$1.html last;
        break;
    }
}
```

## 开启gzip
```
gzip on;
gzip_min_length  2k;
gzip_buffers     4 16k;
gzip_http_version 1.1;
gzip_comp_level 6;
gzip_types     text/plain application/javascript application/x-javascript image/jpeg image/gif image/png text/javascript text/css application/xml;
gzip_vary on;
gzip_proxied   expired no-cache no-store private auth;
gzip_disable   "MSIE [1-6]\.";
```
