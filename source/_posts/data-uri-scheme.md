---
title: Data URI Scheme
date: 2019-09-05 14:12:16
tags:
    - 前端
    - URI
categories:
    - 前端
---

# 基本概念

```
URI（Uniform Resource Identifier）:统一资源标识符,服务器资源名被称为统一资源标识符。
URL（Uniform Resource Locator）:统一资源定位符，描述了一台特定服务器上某资源的特定位置。
URN（Uniform Resource Name）:统一资源名称
```

# 组成

```
协议://主机名[:端口]/ 路径/[:参数] [?查询]#Fragment

protocol :// hostname[:port] / path / [:parameters][?query]#fragment
```

## 格式规范

```
data:[<mime type>][;charset=<charset>][;<encoding>],<encoded data>

1.  data ：协议名称；

2.  [<mime type>] ：可选项，数据类型（image/png、text/plain等）

3.  [;charset=<charset>] ：可选项，源文本的字符集编码方式

4.  [;<encoding>] ：数据编码方式（默认US-ASCII，BASE64两种）

5.  ,<encoded data> ：编码后的数据
```

## 支持的类型

```
data:,                            文本数据
data:text/plain,                    文本数据
data:text/html,                  HTML代码
data:text/html;base64,            base64编码的HTML代码
data:text/css,                    CSS代码
data:text/css;base64,              base64编码的CSS代码
data:text/javascript,              Javascript代码
data:text/javascript;base64,        base64编码的Javascript代码
data:image/gif;base64,            base64编码的gif图片数据
data:image/png;base64,            base64编码的png图片数据
data:image/jpeg;base64,          base64编码的jpeg图片数据
data:image/x-icon;base64,          base64编码的icon图片数据
```

# 优缺点

## 优点

```
1. 减少资源请求链接数。
2. 当访问外部资源很麻烦或受限时，可以很好的利用Data URI Scheme
```

## 缺点

```
1. Data URL形式的图片不会被浏览器缓存，这意味着每次访问这样页面时都被下载一次，
   但可通过在css文件的background-image样式规则使用Data URI Scheme，使其随css文件一同被浏览器缓存起来）。
2. Base64编码的数据体积通常是原数据的体积4/3，
   也就是Data URL形式的图片会比二进制格式的图片体积大1/3。
3. 移动端性能比较低。
```
