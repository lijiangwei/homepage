---
title: editorconfig
date: 2018-08-07 11:41:13
tags:
    - editor
    - editorconfig
    - 代码规范
categories:
    - editor
---

> 使用editorconfig配置文件统一代码规范，vs code 默认不支持`.editconfig`文件，需要安装`EditorConfig`插件

# 安装EditorConfig插件

```
# 打开命令窗口
command + shift + p

# 搜索editorconfig
```

# editorconfig配置

| 配置 | 值 | 描述 |
| ------ | ------ | ------ |
| indent_style |`tab` `space` | Indentation Style |
| indent_size | `an integer` `tab` | Indentation Size (in single-spaced characters) |
| tab_width | `a positive integer (defaults indent_size when indent_size is a number)` | Width of a single tabstop character |
| end_of_line | `lf` `crlf` `cr` | Line ending file format (Unix, DOS, Mac) |
| charset | `utf-8` | File character encoding |
| trim_trailing_whitespace | `true` `false` | Denotes whether whitespace is allowed at the end of lines |
| insert_final_newline | `true` `false` | Denotes whether file should end with a newline |

