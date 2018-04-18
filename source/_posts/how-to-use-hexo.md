---
title: Hexo使用教程
date: 2018-04-18 09:38:56
tags:
categories: 
    -技术
---

>Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

## 安装及使用
参考官网教程：[中文官网](https://hexo.io/zh-cn/)

## 主题设置
推荐使用NextT主题[next使用教程](http://theme-next.iissnan.com/)

## Next个性化配置

### 搜索功能
推荐使用Local Search作为站内搜索，搜索速度快，同时比较简洁，启用方法如下：
1. 安装插件
```
npm install hexo-generator-searchdb --save
```
2. 更改配置文件
在配置文件的任意位置增加下面的内容：
```
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```
3. 更改主题的配置文件
开启local search做为站内搜索
```
# Local search
local_search:
  enable: true
```

## 配置页面访问量
修改themes/next目录下的_config.yml配置文件(安装的next主题)
```
# Show PV/UV of the website/page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi/
busuanzi_count:
  # count values only if the other configs are false
  enable: true
  # custom uv span for the whole site
  site_uv: false
  site_uv_header: <i class="fa fa-user"></i> 访问人数
  site_uv_footer:
  # custom pv span for the whole site
  site_pv: true
  site_pv_header: <i class="fa fa-eye"></i> 总访问量
  site_pv_footer: 次
  # custom pv span for one page only
  page_pv: true
  page_pv_header: <i class="fa fa-eye"></i> 浏览
  page_pv_footer: 次
```

## 配置百度统计
1. 申请百度统计的账号、配置域名
申请地址：[https://tongji.baidu.com/web/welcome/login](https://tongji.baidu.com/web/welcome/login)
账号域名填写自己github pages地址：yourname.github.io

2. 修改next主题的配置文件
只需要配置百度统计的Analytics ID
```
# theme/next/_config.yml文件
# Baidu Analytics ID
baidu_analytics: 726d0dd15533fd165eb3a61c78edd605
```
## 集成Gitment评论系统
参考：[https://zonghongyan.github.io/2017/06/29/201706292034/](https://zonghongyan.github.io/2017/06/29/201706292034/)

注意点：
1. githubID输入的是ower，github的用户名，在gitment.swig中取的值，修改gitment.swig中id的值，默认为window.location.href，修改为提交issur的仓库id，例如：4849199，否则提交comment的时候可能会报错
```
https://api.github.com/repos/xxx/xxx.github.io/issues 422 (Unprocessable Entity)
```
## 配置打赏
把收款二维码发到source/images文件夹下，打开主题的_config.yml文件
```
# Reward
reward_comment: 您的支持将鼓励我继续创作！
#wechatpay: /images/wechatpay.jpg
alipay: /images/alipay.jpg
#bitcoin: /images/bitcoin.png
```

### 配置RSS
1. 安装插件
```
npm install hexo-generator-feed
```
2. 修改配置文件_config.yml
使用插件hexo-generator-feed
```
# Extensions
## Plugins: https://hexo.io/plugins/
plugins: hexo-generator-feed
```
3. 修改next主题配置文件
```

```
## 配置友情连接
修改主题的配置文件
```
# Blog rolls
links_title: 友情链接
#links_layout: block
links_layout: inline
links:
  阿里云: https://aliyun.com
```

## 设置网站图标
在[比特虫](http://www.bitbug.net/)制作favicon.ico图标，放到source目录下。
本地测试没有生效，我把图标放到了七牛云存储空间中，访问存储空间中的图片生效了。
```
#使用存储空间的图片，修改主题的配置文件
# Put your favicon.ico into `hexo-site/source/` directory.
favicon: http://p7dkryqvb.bkt.clouddn.com/favicon.ico
```