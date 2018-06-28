---
title: webpack image-webpack-loader
date: 2018-05-31 09:27:04
tags:
    - 前端工具
    - webpack
categories:
    - webpack
---

# 使用image-webpack-loader压缩图片

## 安装
```
npm install image-webpack-loader --save-dev
```

## 配置
```
loaders: [{
  test: /\.(gif|png|jpe?g|svg)$/i,
  use: [
    'file-loader',
    {
      loader: 'image-webpack-loader',
      options: {
        bypassOnDebug: true,
      },
    },
  ],
}]
```

### 可选配置
```
loaders: [{
  test: /\.(gif|png|jpe?g|svg)$/i,
  use: [
    'file-loader',
    {
      loader: 'image-webpack-loader',
      options: {
        mozjpeg: {
          progressive: true,
          quality: 65
        },
        // optipng.enabled: false will disable optipng
        optipng: {
          enabled: false,
        },
        pngquant: {
          quality: '65-90',
          speed: 4
        },
        gifsicle: {
          interlaced: false,
        },
        // the webp option will enable WEBP
        webp: {
          quality: 75
        }
      }
    },
  ],
}]
```

# 使用imagemin-webpack-plugin压缩没有被file-loader处理的图片

## 安装
```
npm install imagemin-webpack-plugin --save-dev
```

## 配置
```
import ImageminPlugin from 'imagemin-webpack-plugin'

module.exports = {
  plugins: [
    // Copy the images folder and optimize all the images
    new CopyWebpackPlugin([{
      from: 'images/'
    }]),
    new ImageminPlugin({ test: /\.(jpe?g|png|gif|svg)$/i })
  ]
}
```