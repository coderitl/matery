---
title: Hexo-添加HTML文件案例
tags: HTML
categories: HTML
top: 2
cover: 'https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/hexo.png'
abbrlink: 56851
date: 2020-10-15 23:24:05
top_img:
---

```html
1. 在 Hexo 博客所在的本地地址 --> source --> 新建存放 HTML 文件的夹 --> 子类问价夹

(index.html,css,js,img)

```

![本地路径](https://img-blog.csdnimg.cn/20201018114518860.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

```html
2. 修改配置文件 _config.yml(在根目录下，不是主题文件夹下的配置文件)

修改：

	skip_render:
			
  		- "ZONE/PageDemo/*" 

		<!-- 新添加注意格式(修改为你本地的路径，，建议路径写全) -->
		
	    <!-- skip_render: 跳过解析的作用 -->

```

```html
3. 修改主题文件夹下的 _config.yml 


menu:
  主页: /
  随笔: /tags/随笔/
  相册: /photos
  分类: /categories
  HTMLDemo: /ZONE/PageDemo/  <!-- 新添加 HTMLDemo -->

```

```bash
4. 提交预览：

	hexo clean 

	hexo g
	
	hexo s (本地预览)
	
	如果出现 4000 端口被占用的情况使用: hexo s -p 新端口号即可
	
	hexo d 
```

```html
5. 过程中出现的问题

+ source 下的子文件夹第一次提交可能不出现，请等待或再次提交 

+ css、js、img 保持原样即可不动

```

