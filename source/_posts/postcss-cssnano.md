---
title: postcss-cssnano
date: 2018-08-03 23:56:37
tags:
    - css
    - postcss
    - cssnano
categories:
    - css
    - postcss
---

# cssnano使用

> 在webpack中使用cssnano压缩css代码，首先需要安装postcss-loader

## 安装

```
npm i cssnano -D
```

## 配置

```
# postcss.config.js
module.exports = {
  parser: 'sugarss',
  plugins: {
    'postcss-import': {},
    'postcss-preset-env': {},
    'cssnano': {}
  }
}
```