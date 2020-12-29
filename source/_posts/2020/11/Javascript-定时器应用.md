---
title: Javascript-定时器应用
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 49781
date: 2020-11-29 16:31:26
top_img:
cover:
---



###  定时器应用

+ `setTimeout`

  ```javascript
  var id =  setTimeout(function(){
              执行程序
          },时间(单位毫秒));
  
  清除定时器:
  	 clearTimeout(id);
  ```

+ `setInterval`

  ```javascript
  var id =  setInterval(function(){
              执行程序
          },时间(单位毫秒));
  
  清除定时器:
  	 clearInterval(id);
  ```

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201201121918743.gif" alt="setInterval" title="setInterval">



+ `css`

  ```less
   div {
              width: 200px;
              height: 150px;
              border: 2px solid #ccc;
              margin: 100px auto;
          }
  
          div>span {
              text-align: center;
              display: inline-block;
              width: 50px;
              height: 50px;
              color: #09f;
              background-color: #eee;
              line-height: 50px;
              margin-top: 25%;
              margin-left: 4.7%;
          }
  ```

+ `html`结构

  ```html
    <div>
          <span class="hour">1</span>
          <span class="minute">2</span>
          <span class="second">3</span>
      </div>
  ```

+ `JS`原理分析

  ```javascript
  // 获取元素
          var hour = document.querySelector('.hour');
          var minute = document.querySelector('.minute');
          var second = document.querySelector('.second');
          var inputTime = +new Date('2020-12-1 22:20:00'); // 返回用户输入的时间总毫秒数
          countDown();
          setInterval(countDown, 1000);
  
          function countDown() {
              var nowTime = +new Date();// 返回当前时间总的毫秒数
              var times = (inputTime - nowTime) / 1000; // times 是剩余时间的总数
              var h = parseInt(times / 60 / 60 % 24); // 时 
              h = h < 10 ? '0' + h : h;
              hour.innerHTML = h;
  
              var m = parseInt(times / 60 % 60);
              m = m < 10 ? '0' + m : m;
              minute.innerHTML = m;
  
              var s = parseInt(times % 60);
              s = s < 10 ? '0' + s : s;
              second.innerHTML = s;
          }
  ```

  

###  发送验证码

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201201130934465.gif" alt="setInterval" title="setInterval">

+ `css`源码

  ```css
   div {
              width: 400px;
              height: 150px;
              border: 2px solid #09f;
              margin: 100px auto;
          }
  
          input {
              border: none;
              outline: none;
              border-bottom: 2px solid red;
              margin-top: 65px;
              margin-left: 20px;
          }
  
          button {
              margin-left: 20px;
          }
  ```

+ `html`结构

  ```html
  <div>
          <label for="input">
              <input type="text" id="input"><button> 发送验证码 </button>
          </label>
      </div>
  ```

+ `JS`原理分析

  ```javascript
  var _input = document.querySelector('input');
          var btn = document.querySelector('button');
          var count = 2;
          btn.addEventListener('click', function () {
              var timer = setInterval(function () {
                  if (count == 0) {
                      clearInterval(timer);
                      btn.innerHTML = '发送验证码';
                      btn.disabled = false;
                      count = 2;
                  }
                  else {
                      btn.disabled = true;
                      btn.innerHTML = '还剩余' + count + '秒'
                      count--;
                  }
              }, 1000);
          }); 
  ```

  