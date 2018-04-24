---
title: 上传图片预览
date: 2018-04-24 10:12:10
tags:
    - html
    - img
categories:
    - 前端
---

图片上传前预览本地图片的几种方法，假设input[type=file]的id是fileupload，预览的img标签的id是preview。
1. 使用FileReader
```
if(window.FileReader) {
    var file = document.getElementById("fileupload");
    var fr = new FileReader();
    fr.onloadend = function(e) {
        document.getElementById("preview").src = e.target.result;
    }
    fr.readAsDataURL(file.files[0]);
}
```

2. 使用createObjectURL
```
var file = document.getElementById("fileupload");
var url = window.URL.createObjectURL(file.files[0]);
document.getElementById("preview").src = url;
```

3. IE8、9使用滤镜
```
<!DOCTYPE HTML>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <style type="text/css">
    .image_container {
        width: 48px;
        height: 48px;
        position: relative;
    }
    </style>
    <script type="text/javascript" src="js/jquery.min.js"></script>
    <script language="javascript">
    $(function() {
        $("#file_upload").change(function() {
            var $file = $(this);
            var fileObj = $file[0];
            var windowURL = window.URL || window.webkitURL;
            var dataURL;
            var $img = $("#preview");
 
            if(fileObj && fileObj.files && fileObj.files[0]){
                dataURL = windowURL.createObjectURL(fileObj.files[0]);
                $img.attr('src',dataURL);
            }else{
                //IE8、9获取图片真实路径需要document.selection.createRange().text
                $file[0].select();
                $file[0].blur();
                dataURL = document.selection.createRange().text
                // dataURL = $file.val();
                var imgObj = document.getElementById("preview");
                // 两个坑:
                // 1、在设置filter属性时，元素必须已经存在在DOM树中，动态创建的Node，也需要在设置属性前加入到DOM中，先设置属性在加入，无效；
                // 2、src属性需要像下面的方式添加，上面的两种方式添加，无效；
                imgObj.style.filter = "progid:DXImageTransform.Microsoft.AlphaImageLoader(sizingMethod=scale)";
                imgObj.filters.item("DXImageTransform.Microsoft.AlphaImageLoader").src = dataURL;
            }
        });
    });
    </script>
</head>
<body>
    <div id="demo">
        <input id="file_upload" type="file" />
        <div class="image_container">
            <img id="preview" width="60" height="60">
        </div>
    </div>
</body>
</html>
```
