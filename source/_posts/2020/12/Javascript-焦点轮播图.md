---
title: Javascript-焦点轮播图
tags: javascript
categories: javascript
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
abbrlink: 50800
date: 2020-12-13 21:34:11
top_img:
cover:
---

###  

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201213213245192.gif" alt="Javascript-焦点轮播图" title="Javascript-焦点轮播图">

+ `css`源码

  ```css
    * {
              margin: 0;
              padding: 0;
          }
  
          .box {
              position: relative;
              display: block;
              width: 640px;
              height: 353px;
              overflow: hidden;
              margin: 100px auto;
          }
  
          .box ul {
              position: absolute;
              list-style: none;
              width: 500%;
          }
  
          .box ul li {
              float: left;
          }
  
          .box ul li a>img {
              display: block;
              width: 640px;
              height: 353px;
          }
  
          .box {
              position: relative;
          }
  
          .box .arrow {
              position: absolute;
              width: 100%;
              height: 100%;
          }
  
          .box .arrow a {
              position: absolute;
              display: block;
              width: 35px;
              height: 40px;
              text-align: center;
              line-height: 40px;
              text-decoration: none;
              color: #fff;
              font-weight: bold;
              background-color: rgba(0, 0, 0, .5);
          }
  
          .box .arrow a:nth-child(1) {
              left: 18px;
              top: 50%;
              transform: translate(-50%);
          }
  
          .box .arrow a:nth-child(2) {
              right: -18px;
              top: 50%;
              transform: translate(-50%);
          }
  
          ol {
              position: absolute;
              right: 20px;
              bottom: 25px;
              list-style: none;
              padding: 6px 10px;
              height: 8px;
              border-radius: 12px;
              background-color: rgba(0, 0, 0, .5);
              line-height: 20px;
          }
  
          ol li {
              float: left;
              width: 8px;
              height: 8px;
              margin: 0 10px;
              background-color: #fff;
              border-radius: 50%;
          }
  
          .box .current {
              background-color: red;
          }
  ```

+ `html`结构

  ```html
  
      <div class="box">
          <ul class="ul">
              <li><a href="#"><img src="img/01.jpg" alt=""></a></li>
              <li><a href="#"><img src="img/02.jpg" alt=""></a></li>
              <li><a href="#"><img src="img/03.jpg" alt=""></a></li>
              <li><a href="#"><img src="img/04.jpg" alt=""></a></li>
          </ul>
          <div class="arrow">
              <a href="javascript:;" class="prev"> &lt; </a>
              <a href="javascript:;" class="next"> &gt; </a>
          </div>
          <ol>
              <!-- 
                  <li></li>
                  <li></li>
                  <li></li>
           -->
          </ol>
      </div>
  ```

+ `JS`原理分析

  ```javascript
   // 获取元素
          var _ul = document.querySelector('.ul');
          var _ol = document.querySelector('ol');
          // 获取左右箭头
          var prev = document.querySelector('.prev');
          var next = document.querySelector('.next');
  
  
          var box = document.querySelector('.box');
          //ImgoffsetWidth = -( 图片宽度 * 索引号);
          var boxWidth = box.offsetWidth;
          // console.log(boxWidth);
  
          // 小圆圈函数
          // 获取图片张数
          var imgs = _ul.children;
          // console.log(imgs);
          for (var i = 0; i < imgs.length; i++) {
              //动态生成小圆圈
              var lis = document.createElement('li');
              // 设置索引号
              lis.setAttribute('index', i);
              _ol.appendChild(lis);
              // li 的点击事件
              lis.addEventListener('click', function () {
                  // 根据图片张数限制小圆圈个数 排它思想
                  for (var i = 0; i < _ol.children.length; i++) {
                      // 需过后理解
                      _ol.children[i].className = '';
                  }
                  this.className = 'current';
                  // 小圆圈点击事件时 图片移动
                  // 获取自定义属性
                  var index = this.getAttribute('index');
                  num = index;
                  circle = index;
                  // console.log(boxWidth); 640 
                  animation(_ul, -index * boxWidth);
              });
          }
          // 让 ol>li 添加 current 类  
          _ol.children[0].className = 'current';
          //  克隆节点 ul li:first true 深度克隆 节点及内容全部克隆
          var first = _ul.children[0].cloneNode(true);
          _ul.appendChild(first);
  
          // circle 控制小圆圈的播放
          var circle = 0;
          var num = 0;
  		// 节流阀
  		var flag = true;
          // 上一张
          prev.addEventListener('click', function () {
              if(flag){
                  flag = false;
                 // 0 第一张
              if (num == 0) {
                  num = _ul.children.length - 1;
                  _ul.style.left = -num * boxWidth + 'px';
              }
              num--;
              // 谁做动画为 obj
              animation(_ul, -num * boxWidth,function(){
                  flag = true;
              });
  
              // 小圆圈跟随 
              circle--;
              if (circle < 0) {
                  circle = _ol.children.length - 1;
              }
  
              circleChange();
                 }
          });
  
          // 下一张
          next.addEventListener('click', function () {
            if(flag){
                flag = false;
                  // 
              if (num == _ul.children.length - 1) {
                  _ul.style.left = 0;
                  num = 0;
              }
              num++;
              // 谁做动画为 obj
              animation(_ul, -num * boxWidth,function(){
                  flag = true;
              });
  
              // 小圆圈跟随 
              circle++;
              if (circle == _ol.children.length) {
                  circle = 0;
              }
  
              circleChange();
            }
          });
  
          function circleChange() {
              for (var i = 0; i < _ol.children.length; i++) {
                  // 需过后理解
                  _ol.children[i].className = '';
              }
              _ol.children[circle].className = 'current';
          }
  
   		// 自动播放
          var timer = setInterval(function () {
              next.click();
          }, 2000);
          // 鼠标移入停止计时器
          box.addEventListener('mouseenter', function () {
              clearInterval(timer);
              timer = null;
          });
          box.addEventListener('mouseleave', function () {
              timer = setInterval(function () {
                  next.click();
              }, 2000);
          });
  
  ```

+ 动画函数的封装与应用

  ```javascript
  animation(obj,target,collback);
  ```

  ​                                    