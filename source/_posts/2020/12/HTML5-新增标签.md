---
title: HTML5-新增标签
tags:
  - HTML5
  - 网页优化
abbrlink: 50583
date: 2020-12-29 11:20:35
---

###   HTML5-新增标签

####  语义化标签

1. `<header>` 头部标签
2. `<nav>` 导航标签
3. `<article>`  内容标签
4. `<section>` 块级标签
5.  `<aside>` 侧边栏标签
6.  `<footer>` 尾部标签

####  音频标签

```html
<audio>
```

|     格式     | IE9  | Firefox3.5 | Opera10.5 | Chrome3.0 | Safari3.0 |
| :----------: | :--: | :--------: | :-------: | :-------: | :-------: |
| `Ogg Vorbis` |      |     ✓      |     ✓     |     ✓     |           |
|    `MP3`     |  ✓   |            |           |     ✓     |     ✓     |
|    `Wav`     |      |     ✓      |     ✓     |           |     ✓     |

|    属性    |     值     |                     描述                     |
| :--------: | :--------: | :------------------------------------------: |
| `autoplay` | `autoplay` |    如果出现该属性,则音频在就绪后马上播放     |
| `controls` | `controls` | 如果出现该属性,则向用户显示控件,比如播放按钮 |
|   `loop`   |   `loop`   | 如果出现该属性,则每当音频结束时重新开始播放  |
|   `src`    |   `url`    |             要播放的音频的 `URL`             |

```html
<audio src="path/···"  controls="controls"> </audio>

+ 兼容性写法
<audio>
    <source src="path/···" type="audio/mepg">
    <source src="path/···" type="audio/ogg">
</audio>
```

####  视频标签

```html
<video>
```

```html
 <video autoplay=“autoplay”>
	<source src="path/···" type="video/mp4">
    <source src="path/···" type="video/ogg">
</video>

属性: width,height,loop,preload( auto预加载，none 不应加载视频),src,poster
```

###  HTML5表单

```html
<input type="email" />

input: 
    type="email" 限制用户输入为 Email 类型

    type="tel" 手机号码
    type="number" 限制用户输入必须为数字类型
    type="search" 搜索框

    type="url" 限制用户输入必须为 URL
    type="time" 限制用户输入必须为时间类型
	type="color" 生成一个颜色先择表单
	type="date" 限制用户输入必须为日期类型
```

###  命名规范

```bash
命名作用:
	添加样式
	js 控制元素对象
	id="" 身份证 具有唯一性
	class="" 同名同姓,多个
命名规范:
	1. 字母开头 数字 横线
	2. 见名知意 通俗易懂
```

###  优化

+ 图片优化

  ```html
  <img src="" width="" hieght="" alt="关键词">
  ```

