---
title: Hexo使用教程
tags:
  - Hexo
  - Next
categories:
  - 技术
abbrlink: b8d83faa
date: 2018-04-18 09:38:56
---

>Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

## 安装及使用
参考官网教程：[中文官网](https://hexo.io/zh-cn/)

## 主题设置
推荐使用NexT主题[next使用教程](http://theme-next.iissnan.com/getting-started.html)

## 设置中文
修改配置文件(_config.yml)
```
language: zh-Hans
```

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

<!-- more -->

### 设置动态背景
***效果图***
![](http://p7dkryqvb.bkt.clouddn.com/next_bg.gif)
从下面选择喜欢的背景
```
#修改主题配置文件
# Canvas-nest
canvas_nest: true

# three_waves
three_waves: false

# canvas_lines
canvas_lines: false

# canvas_sphere
canvas_sphere: false
```

### 点击出现桃心
***效果图***
![](http://p7dkryqvb.bkt.clouddn.com/next_click.gif)
下载[love.js](http://7u2ss1.com1.z0.glb.clouddn.com/love.js)保存到`/themes/next/source/js/src`，在`\themes\next\layout\_layout.swig`文件末尾进入js文件
```
<!-- 页面点击小红心 -->
<script type="text/javascript" src="/js/src/love.js"></script>
```

### 修改链接样式
在`themes\next\source\css\_common\components\post\post.styl`在末尾添加如下css样式：
```
// 文章内链接文本样式
.post-body p a{
  color: #0593d3;
  border-bottom: none;
  border-bottom: 1px solid #0593d3;
  &:hover {
    color: #fc6423;
    border-bottom: none;
    border-bottom: 1px solid #fc6423;
  }
}
```

### 修改标签样式
修改模版`/themes/next/layout/_macro/post.swig`，把`rel="tag">#`替换为`<i class="fa fa-tag"></i>`

### 配置页面访问量
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

### 配置百度统计
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
### 集成Gitment评论系统
参考：[https://zonghongyan.github.io/2017/06/29/201706292034/](https://zonghongyan.github.io/2017/06/29/201706292034/)

注意点：
1. githubID输入的是ower，github的用户名，在gitment.swig中取的值，修改gitment.swig中id的值，默认为window.location.href，修改为提交issur的仓库id，例如：4849199，否则提交comment的时候可能会报错
```
https://api.github.com/repos/xxx/xxx.github.io/issues 422 (Unprocessable Entity)
```
### 配置打赏
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
# Set rss to false to disable feed link.
# Leave rss as empty to use site's feed link.
# Set rss to specific value if you have burned your feed already.
rss: /atom.xml
```
### 配置友情连接
修改主题的配置文件
```
# Blog rolls
links_title: 友情链接
#links_layout: block
links_layout: inline
links:
  阿里云: https://aliyun.com
```

### 设置网站图标
在[比特虫](http://www.bitbug.net/)制作favicon.ico图标，放到source目录下。
本地测试没有生效，我把图标放到了七牛云存储空间中，访问存储空间中的图片生效了。
```
#使用存储空间的图片，修改主题的配置文件
# Put your favicon.ico into `hexo-site/source/` directory.
favicon: http://p7dkryqvb.bkt.clouddn.com/favicon.ico
```

### 修改行内代码块样式
在`\themes\next\source\css\_custom\custom.styl`文件中增加样式
```
// Custom styles.
code {
    color: #ff7600;
    background: #fbf7f8;
    margin: 2px;
}
// 大代码块的自定义样式
.highlight, pre {
    margin: 5px 0;
    padding: 5px;
    border-radius: 3px;
}
.highlight, code, pre {
    border: 1px solid #d6d6d6;
}
```

### 主页文章添加阴影效果
`\themes\next\source\css\_custom\custom.styl`文件增加样式
```
// 主页文章添加阴影效果
.post {
  margin-top: 60px;
  margin-bottom: 60px;
  padding: 25px;
  -webkit-box-shadow: 0 0 5px rgba(202, 203, 203, .5);
  -moz-box-shadow: 0 0 5px rgba(202, 203, 204, .5);
}
```

### 添加热度
***效果***
![](http://p7dkryqvb.bkt.clouddn.com/next_hot_effect.png)
打开`/themes/next/layout/_macro/post.swig`,在画红线的区域添加`℃`
![](http://p7dkryqvb.bkt.clouddn.com/next_hot_html.png)
打开`/themes/next/languages/zh-Hans.yml`将画红框的改为热度
![](http://p7dkryqvb.bkt.clouddn.com/next_hot_zh.png)
修改主题配置文件
```
# Show number of visitors to each article.
# You can visit https://leancloud.cn get AppID and AppKey.
leancloud_visitors:
  enable: true
  app_id: 
  app_key: 
```
填入自己的app_id和app_key，没有的话在[leancloud](https://leancloud.cn)上注册并创建应用会分配app_id、app_key。

### 增加字数统计
安装`hexo-wordcount`插件
```
npm install hexo-wordcount --save
```
在`/themes/next/layout/_partials/footer.swig`文件尾部加上
```
<div class="theme-info">
  <div class="powered-by"></div>
  <span class="post-count">全站共{{ totalcount(site) }}字</span>
</div>
```

### 字数统计
修改主题配置文件
```
# Post wordcount display settings
# Dependencies: https://github.com/willin/hexo-wordcount
post_wordcount:
  item_text: true
  wordcount: true
  min2read: true
  separated_meta: true
```

### 显示进度条
```
# Progress bar in the top during page loading.
pace: true
# Themes list:
#pace-theme-big-counter
#pace-theme-bounce
#pace-theme-barber-shop
#pace-theme-center-atom
#pace-theme-center-circle
#pace-theme-center-radar
#pace-theme-center-simple
#pace-theme-corner-indicator
#pace-theme-fill-left
#pace-theme-flash
#pace-theme-loading-bar
#pace-theme-mac-osx
#pace-theme-minimal
# For example
# pace_theme: pace-theme-center-simple
pace_theme: pace-theme-minimal
```

## 压缩代码
使用gulp压缩js、css代码
```
npm install gulp -g
npm install gulp-minify-css gulp-uglify gulp-htmlmin gulp-htmlclean gulp --save
```
新建`gulpfile.js`文件
```
var gulp = require('gulp');
var minifycss = require('gulp-minify-css');
var uglify = require('gulp-uglify');
var htmlmin = require('gulp-htmlmin');
var htmlclean = require('gulp-htmlclean');
// 压缩 public 目录 css
gulp.task('minify-css', function() {
    return gulp.src('./public/**/*.css')
        .pipe(minifycss())
        .pipe(gulp.dest('./public'));
});
// 压缩 public 目录 html
gulp.task('minify-html', function() {
  return gulp.src('./public/**/*.html')
    .pipe(htmlclean())
    .pipe(htmlmin({
         removeComments: true,
         minifyJS: true,
         minifyCSS: true,
         minifyURLs: true,
    }))
    .pipe(gulp.dest('./public'))
});
// 压缩 public/js 目录 js
gulp.task('minify-js', function() {
    return gulp.src('./public/**/*.js')
        .pipe(uglify())
        .pipe(gulp.dest('./public'));
});
// 执行 gulp 命令时执行的任务
gulp.task('default', [
    'minify-html','minify-css','minify-js'
]);
```
`hexo g`生成代码后执行`gulp`命令优化静态资源

## 添加README.md文件
在Hexo工程的`source`目录下添加一个`README.md`文件，修改站点配置文件`_config.yml`，将`skip_render`参数的值设置为
```
skip_render: README.md
```