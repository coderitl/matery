---
title: ImageHover-scale
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
categories: css
abbrlink: 6923
date: 2020-11-29 15:37:22
tags:
top_img:
cover:
---

###  前端鼠标划入图片原位放大

+ 效果演示
![鼠标滑入图片原位放大](https://img-blog.csdnimg.cn/20201129153425915.gif#pic_center)

+  `css`源码:
```css
* {
            margin: 0;
            padding: 0;
        }

        body {
            background-color: #ccc;
        }

        .box {
            position: relative;
            width: 533px;
            margin: 100px auto;
        }

        a {
            box-sizing: border-box;
            display: block;
            width: 533px;
            height: 300px;
            overflow: hidden;
            border: 3px solid red;
        }

        img {
            vertical-align: middle;
            width: 533px;
            height: 300px;
            transition: all .5s;
        }

        span {
            position: absolute;
            display: block;
            width: 533px;
            height: 300px;
            background-color: rgba(0, 0, 0, .5);
            top: 0;
            left: 0;
            opacity: 0;
            z-index: -1;
        }

        .box:hover img {
            transform: scale(1.3);
        }

        .box:hover span {
            opacity: .5;
            z-index: 1;
        }
```

+ `html`结构: 
```html
<div class="box">
        <a href="javascript:;"><img src="img/dream.jpg" alt=""></a>
        <span></span>
</div>
```