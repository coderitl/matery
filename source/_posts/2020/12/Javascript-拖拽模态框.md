---
title: Javascript-拖拽模态框
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 332
date: 2020-12-05 17:36:42
top_img:
cover:
---

###  Javascript-拖拽模态框

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/2020120517480142.gif" width="600">

+ 原理分析

  > + 获取模态框在鼠标按下时的坐标位置
  >
  > + `mousedown`
  > + `mousemove`
  > + `mouseup`

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/motaikuang.png" width="600" alt="红色为 document 黑色为模态框" title="红色为 document 黑色为模态框">

+ `css`源码

  ```less
    body {
              background-color: #85C1E9;
          }
  
          .content {
              width: 996px;
              margin: 100px auto;
              position: relative;
              /*  出生点  */
              left: 50%;
              top: 50%;
              transform: translate(-50%, -50%);
          }
  
          .box {
              position: absolute;
              width: 600px;
              height: 400px;
              border-radius: 20px;
              background-color: rgba(0, 0, 0, .3);
          }
  
          .box input {
              display: block;
              width: 200px;
              height: 35px;
              line-height: 35px;
              border: none;
              background: none;
              outline: none;
              margin-top: 30px;
              border-bottom: 2px solid red;
          }
  
          .box input[type="submit"] {
              color: #fff;
              margin-top: 30px;
              border: 2px solid #fff;
          }
  
          .box input::placeholder {
              color: #fff;
          }
  
          input:focus::-webkit-input-placeholder {
              color: red;
              font-size: 12px;
              transition: all .5s;
          }
  
          .box .title {
              position: absolute;
              left: 50%;
              transform: translate(-50%);
              font-size: 30px;
              color: #fff;
              font-weight: 700;
              padding-bottom: 20px;
          }
  
          .formInfo {
              position: absolute;
              left: 50%;
              top: 20%;
              transform: translate(-50%);
          }
  
          a {
              position: absolute;
              right: -13px;
              top: -20px;
              display: block;
              width: 40px;
              height: 40px;
              text-decoration: none;
              line-height: 40px;
              text-align: center;
              border-radius: 50%;
              background: #fff;
          }
  ```

+ `html`结构

  ```html
  
      <div class="content">
          <div class="box">
              <a href="javascript:;">X</a>
              <p class="title">
                  拖动模态框实现
              </p>
              <div class="formInfo">
  
                  <input type="text" id="text" placeholder="用户名">
                  <input type="password" name="" id="pwd" placeholder="密码">
                  <input type="submit" value="Login">
              </div>
          </div>
      </div>
  
  ```

+ `JS`原理分析

  ```javascript
    // 获取 box 
          var box = document.querySelector('.box');
  
          // 鼠标按下事件
          box.addEventListener('mousedown', function (e) {
              /* 
                  按下获取当前的坐标:
                      X = e.pageX - box.offsetLeft;
                      Y = e.pageY - box.offsetTop;
              */
              var x = e.pageX - box.offsetLeft;
              var y = e.pageY - box.offsetTop;
              // console.log(x, y);
              // 移动事件
              document.addEventListener('mousemove', move);
              function move(e) {
                  /*
                 在盒子内点击时获取的坐标是固定不变的 移动
             */
                  box.style.left = e.pageX - x + 'px';
                  box.style.top = e.pageY - y + 'px';
              }
              // 鼠标抬起事件
              document.addEventListener('mouseup', function () {
                  document.removeEventListener('mousemove', move);
              });
          });
  ```

  