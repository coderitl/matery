---
title: Javascript-获取页面坐标
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 7982
date: 2020-11-29 12:05:52
top_img:
cover:
---

###  鼠标事件对象

| 鼠标事件对象 |                    说明                    |
| :----------: | :----------------------------------------: |
| `e.clientX`  |  返回鼠标相对于浏览器窗口可视区的 X 坐标   |
| `e.clientY`  |  返回鼠标相对于浏览器窗口可视区的 Y 坐标   |
|  `e.pageX`   | 返回鼠标相对于文档页面的 X 坐标 `IE9+支持` |
|  `e.pageY`   | 返回鼠标相对于文档页面的 Y 坐标 `IE9+支持` |
| `e.screenX`  |      返回鼠标相对于电脑屏幕的 X 坐标       |
| `e.screenY`  |      返回鼠标相对于电脑屏幕的 XY坐标       |

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201129123224588.gif" title="mousemove" alt="mousemove">

+ `css`源码

  ```less
   img {
              position: absolute; // **
              width: 160px;
          }
  ```

+ `html`结构

  ```html
  <div>
          <img src="img/mousemove.png" alt="">
  </div>
  ```

+ `JS`原理分析

  ```javascript
    <script>
          // 获取元素 img
          var photo = document.querySelector('img');
          document.addEventListener('mousemove', function (e) {
              // pageX  pageY
              var photoX = e.pageX + 'px';
              var photoY = e.pageY + 'px';
              // 给图片添加 style 改变 left top
              photo.style.left = photoX;
              photo.style.top = photoY;
          });
  ```

  

