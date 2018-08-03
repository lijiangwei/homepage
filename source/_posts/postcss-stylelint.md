---
title: postcss-stylelint
date: 2018-08-04 00:10:10
tags:
    - css
    - postcss
    - stylelint
categories:
    - css
    - postcss
---

> 在webpack中使用stylelint规范css写法

# 在editor中安装stylelint

## vscode安装stylelint插件

```
1、command + shift + p 打开命令窗口
2、输入Install Extensions
3、搜索 @sort:installs stylelint
# 安装stylelint插件
```

## 配置插件

设置user setting或者workspace setting，关闭系统对css的校验

```
"css.validate": false,
"less.validate": false,
"scss.validate": false
```

## 配置文件

```
# 安装配置规则
npm install stylelint-config-standard --save-dev

# 新建配置文件.stylelintrc
{
  "extends": "stylelint-config-standard"
}
```

## 格式化文件

```
stylelint --fix
```

## 安装格式化插件

vscode安装 `stylefmt`

# webpack集成stylelint

## 安装stylelint

```
npm install stylelint -D
```

## 修改postcss配置文件

```
module.exports = {
  plugins: [
    require('autoprefixer')({
      browsers: ['last 5 versions']
    }),
    require('cssnano')({}),
    require('stylelint')({})
  ]
}
```
