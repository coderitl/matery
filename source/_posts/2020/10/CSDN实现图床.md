---
title: CSDN实现图床
date: 2020-10-19 15:50:27
tags: 图床
top: 2
type: "categories"
categories:
- 图床
top_img:
cover: https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/picPhoto.png
---

### 根目录下的`source/`添加静态资源文件夹：

+ 添加不被渲染的主文件夹
+ 在主文件夹下添加子文件夹 / ( `idnex.html,css,js`)



### 添加友情链接：

```css
smart_menu:
  innerArchive: '所有文章'
  friends: '友情链接'
  aboutme: '关于'

friends:
    media媒体查询: https://lovobin.github.io/ZONE/PageDemo/
    Flex弹性布局: https://lovobin.github.io/ZONE/QQ-Nav/

```

```html
友情链接的作用: 通过友情链接实现静态资源 demo 的在线预览 


主要文件是；

	html + css + js + image

```



### 图床的实现；

+ 繁琐方式

  ```css
  通过 CSDN 上传图片获取 图片外连接 
  ```

+ 图床效果

  ![实现图床](https://img-blog.csdnimg.cn/20201019144153499.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

+ 步骤演示

  ![步骤演示](https://img-blog.csdnimg.cn/20201019144425216.gif#pic_center)