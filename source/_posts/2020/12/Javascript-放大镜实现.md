---
title: Javascript-放大镜实现
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 10945
date: 2020-12-06 19:21:12
top_img:
cover:
---

###   Javascript-放大镜实现原理分析

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201206192607123.gif" alt="Javascript-放大镜实现原理分析" title="Javascript-放大镜实现原理分析">

+ `css`实现源码

  ```css
  * {
              margin: 0;
              padding: 0;
          }
  
          .box {
              position: relative;
              display: block;
              width: 400px;
              box-sizing: border-box;
          }
  
          .box img {
              vertical-align: middle;
          }
  
          .imgBox {
              border: 1px solid red;
              width: 400px;
          }
  
          .imgBox>img {
              width: 400px;
          }
  
          .mask {
              display: none;
              position: absolute;
              top: 0;
              left: 0;
              right: 0;
              width: 200px;
              height: 200px;
              cursor: move;
              background: rgba(0, 0, 0, .5);
          }
  
          .bigImg {
              display: none;
              position: absolute;
              left: 410px;
              top: 0;
              width: 500px;
              height: 500px;
              overflow: hidden;
              border: 2px solid green;
          }
  
          .bigImg>img {
              width: 500px;
              height: 500px;
          }
  
          .bigMove {
              position: absolute;
          }
  ```

+ `html`结构

  ```html
   <div class="box">
          <div class="imgBox">
              <img src="../mousemove.png" alt="">
          </div>
          <div class="mask"></div>
          <div class="bigImg">
              <img src="../mousemove.png" alt="" class="bigMove">
          </div>
      </div>
  
  ```

+ `JS`原理分析

  ```javascript
  // 获取元素: imgBox mask bigImg
          var mask = document.querySelector('.mask');
          var bigImg = document.querySelector('.bigImg');
          // 鼠标滑入: imgBox 显示 mask 和 bigImg
          var box = document.querySelector('.box');
          // 获取大图片
          var bigMove = document.querySelector('.bigMove');
          // 鼠标划入事件
          box.addEventListener('mouseover', function () {
              mask.style.display = 'block';
              bigImg.style.display = 'block';
          });
  
          // 鼠标移出事件
          box.addEventListener('mouseout', function () {
              mask.style.display = 'none';
              bigImg.style.display = 'none'
          });
  
          // 鼠标移动: mask 遮罩
          // mask 上按下的鼠标事件 mousedown
          mask.addEventListener('mousedown', function (e) {
              // mask 盒子内页面点击时的坐标 = 点击时的坐标 - 盒子左侧偏移量;
              // mask 盒子内页面点击时的坐标 = 点击时的坐标 - 盒子顶部偏移量;
              var x = e.pageX - mask.offsetLeft;
              var y = e.pageX - mask.offsetLeft;
              console.log(x, y);
              // 拖动 mask 的监听事件 
              mask.addEventListener('mousemove', move);
  
              // mask 移动事件
              function move(e) {
                  // mask 的移动怎么获取？
                  // 当前的 e.pageX 个人暂时理解为 相当于在 document 上的点击
                  mask.style.left = e.pageX - x + 'px';
                  mask.style.top = e.pageY - y + 'px';
  
                  // 左侧限制移动范围:
                  // 可移动左侧 = 最大盒子的宽度 - mask 宽度
                  // 可移动下侧 = 最大盒子的宽度 - mask 宽度
                  if (mask.offsetLeft <= 0) {
                      mask.style.left = 0;
                  }
                  // 右侧移动范围限制
                  var maxOffset = box.offsetWidth - mask.offsetWidth;
                  if (mask.offsetLeft >= maxOffset) {
                      mask.style.left = maxOffset + 'px';
                  }
                  // 顶部移动范围限制
                  if (mask.offsetTop <= 0) {
                      mask.style.top = 0;
                  }
                  // 顶部移动范围限制
                  if (mask.offsetTop >= maxOffset) {
                      mask.style.top = maxOffset + 'px';
                  }
  
  
                  /*
                   mask 影响大盒子移动
                      bigImg--> div 
                      bigMove --> 大图片
                  */
                  bigMove.style.left = -e.pageX + 'px';
                  bigMove.style.top = -e.pageY + 'px';
              }
  
              // mask 鼠标抬起事件
              mask.addEventListener('mouseup', function (e) {
                  // 监听移动事件 移除该方法 取消事件绑定
                  mask.removeEventListener('mousemove', move);
              });
          });
  ```

  