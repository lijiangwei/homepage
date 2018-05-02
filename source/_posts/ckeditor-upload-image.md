---
title: ckeditor集成上传图片功能
date: 2018-04-27 10:14:59
tags:
    - ckeditor
    - upload img
categories:
    - 前端
---

# 增加左右对齐功能
下载时增加Justify、Enhanced Image插件

# 上传图片功能
修改配置文件`ckedirot/plugins/image/dialogs/images.js`
```
# 修改下面的hidden值修改为0
id:"Upload",hidden:0

# 删除预览文字
config.image_previewText后面的值删除
```
