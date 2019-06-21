---
title: U盘图标制作
date: 2019-06-21 13:10:36
tags:
---

# U盘图标制作

### 图片准备

* [打开链接](http://www.bitbug.net/)制作ico格式的图标
* 目标尺寸选择（我选择64*64）

### 配置文件准备

* 新建一个txt文档，添加以下内容

  ```
  [autorun]
  ICON=favicon.ico,0
  ```

  favicon是图片名

* 保存为autorun.inf

### 制作

* 将图片和刚刚新建的文件移动到U盘的根目录下
* 如果想彻底隐藏这两个文件可以使用attrib命令[使用方法](https://blog.csdn.net/whatday/article/details/52752555)



### 