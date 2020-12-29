---
title: Javascript-表单校验
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 35364
date: 2020-12-05 00:11:27
top_img:
cover:
---

###   Javascript-表单校验

+ 局部效果演示

  <img src="https://img-blog.csdnimg.cn/20201205001444984.gif" alt="Javascript-表单校验" title="Javascript-表单校验" width="600">

+ `css`源码

  ```less
  
          body {
              background-color: #34495e;
          }
  
          fieldset {
              width: 600px;
              height: 400px;
              color: #fff;
              box-shadow: 0 0 20px rgba(255, 255, 255, .5);
              border: 2px solid #ccc;
              margin: 100px auto;
          }
  
          legend {
              padding: 5px;
          }
  
          input {
              margin: 20px;
              width: 220px;
              height: 35px;
              border: none;
              background: none;
              line-height: 35px;
              outline: none;
              color: #fff;
              border-bottom: 2px solid red;
          }
  
          input::placeholder {
              color: #fff;
          }
  
          fieldset .formTitle {
              display: block;
              width: 100%;
              height: 50px;
              line-height: 50px;
              font-size: 30px;
              font-weight: 700;
              padding: 20px;
              text-align: center;
          }
  
          fieldset p {
              position: relative;
              height: 35px;
              line-height: 35px;
              padding-left: 110px;
          }
  
          fieldset p img {
              display: inline-block;
              vertical-align: middle;
              width: 16px;
              height: 16px;
              line-height: 16px;
          }
  
          fieldset #btn {
              color: #fff;
              font-weight: bold;
              margin-top: 50px;
              height: 35px;
              border-radius: 20px;
              text-align: center;
              line-height: 35px;
              border: 1px solid #ecf0f1;
          }
  
          fieldset .showImg {
              position: absolute;
              right: 153px;
              top: 25px;
              display: none;
          }
  
          fieldset .showImg i {
              display: inline-block;
              font-size: 14px;
              color: rgb(26, 250, 41);
              font-style: normal;
              height: 35px;
              line-height: 35px;
              vertical-align: middle;
              padding-bottom: 6px;
          }
  
          /* 正确状态显示 */
          .true {
              display: inline-block;
              width: 16px;
              height: 16px;
              color: rgb(26, 250, 41);
              background: url('true.png') center center/cover no-repeat;
  
          }
  
          /* 输入错误显示的状态 */
          .false {
              display: inline-block;
              width: 16px;
              height: 16px;
              color: red;
              background: url('false.png') center center/cover no-repeat;
          }
  
          /* 第一次提示时的状态 */
          .caveat {
              display: inline-block;
              width: 16px;
              height: 16px;
              color: yellow;
              background: url('caveat.png') center center/cover no-repeat;
          }
  ```

  

+ `html`结构

  ```html
  
      <form action="#">
          <fieldset>
              <legend> Legend Title </legend>
              <span class="formTitle">Beautify the form</span>
              <p>
                  <input type="text" value="用户名" id="userName">
                  <span class="showImg">
                      <span class="true"></span>
                      <i class="text"> </i>
                  </span>
              </p>
              <p>
                  <input type="password" name="" id="userPassword" placeholder="密码">
                  <span class="showImg">
                      <span class="true"></span>
                      <i class="text"> </i>
                  </span>
              </p>
              <p> <input type="submit" value="登录" id="btn"></p>
          </fieldset>
      </form>
  ```

  

+ `JS`原理分析

  ```javascript
    // 获取用户名输入框
          var userName = document.querySelector('#userName');
          // 获取密码框
          var userPassword = document.querySelector('#userPassword');
          // 获取图片提示
          var showImg = document.querySelector('.showImg');
          // 获取文本提示信息
          var text = document.querySelector('.text');
          // 获取当前状态
          var changeImg = document.querySelector('.true');
  
          // 封装一个函数 传入参数为 提示信息内容,当前文字颜色,当前状态图
          function difText(textInfo, textcolor, _className) {
              showImg.style.display = 'block';
              text.innerHTML = textInfo;
              text.style.color = textcolor;
              changeImg.className = _className;
          }
  
          // 获取 input 的点击事件 
          userName.onfocus = function () {
              // 输入框获取焦点时进行判断是否输入，没有输入的话清空提示信息
              if (userName.value == '用户名') {
                  userName.value = '';
                  difText('请输入', 'yellow', 'caveat');
              }
              // 监听键盘抬起时的事件
              userName.onkeyup = function () {
                  // 如果输入框的用户名为已注册用户 匹配成功时 提示输入正确 否则显示输入错误!
                  if (userName.value === '123') {
                      changeImg.className = 'true';
                      difText('输入正确', 'rgb(26, 250, 41)', 'true');
                  } else {
                      changeImg.className = 'false';
                      difText('输入错误!', 'red', 'false');
                  }
              }
          }
  
          // 失去焦点 
          userName.onblur = function () {
              // 如果没有输入内容 则回复原来的提示信息
              if (userName.value === '') {
                  userName.value = '用户名';
                  // 将提示信息隐藏
                  showImg.style.display = 'none';
              }
          }
  
          // 密码框事件 后续原理大致相同 
  ```

+ 素材下载:
  +  <img src="https://img-blog.csdnimg.cn/20201205002408672.png" width='26'> 
  + <img src="https://img-blog.csdnimg.cn/20201205002408674.png">
  + ![first](https://img-blog.csdnimg.cn/20201205002408670.png)

