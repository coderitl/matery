---
title: JavaScript-封装Tools.js
password: Tools
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 58139
date: 2020-11-29 18:20:03
top_img:
cover:
---



###  拖拽工具类

```javascript
// drag 拖拽 
function drag(node) {
            node.onmousedown = function (ev) {
                // 处理兼容性
                var e = ev || window.event;
                var offsetX = e.clientX - node.offsetLeft;
                var offsetY = e.clientY - node.offsetTop;
                console.log('X:' + offsetX, 'Y' + offsetY);
                document.onmousemove = function (ev) {
                    // 处理兼容性
                    var e = ev || window.event;
                    var l = e.clientX - offsetX;
                    var t = e.clientY - offsetY;
                    // 限制出界
                    if (l <= 0) {
                        l = 0;
                    }
                    var windowsWidth = document.documentElement.clientWidth || document.body.clientWidth;
                    if (l >= windowsWidth - node.offsetWidth) {
                        l = windowsWidth - node.offsetWidthl
                    }
                    if (t <= 0) {
                        t = 0;
                    }
                    var windowsHeight = document.documentElement.clientHeight || document.body.clientHeight;
                    if (t >= windowsHeight - node.offsetHeight) {
                        t = windowsHeight - node.offsetHeight;
                    }
                    node.style.left = l + 'px';
                    node.style.top = t + 'px';
                }
            }
            document.onmouseup = function () {
                document.onmousemove = null;
            }
        }
```



###   倒计时:

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



###  缓动动画封装

+ 左移动

  ```javascript
  /*
  	obj 元素 
  	target 目标距离 
  	callback 回调函数
      spendTime 消耗时间
  */
   function animation(obj, target, spendTime,callback) {
              // 清除定时器 将会只开启一个 定时器
              clearInterval(obj.timer);
              // 物体移动   定时器应用
              obj.timer = setInterval(function () {
                  // 缓动计算公式(step) = (目标值 - 现在的位置) / 10; 
                  var step = (target - obj.offsetLeft) / 10;
                  // 判断 step 正负问题
                  step = step > 0 ? Math.ceil(step) : Math.floor(step);
  
                  if (obj.offsetLeft == target) {
                      clearInterval(obj.timer);
                      // 回调函数应用
                      if (callback) {
                          callback();
                      }
                  }
                  obj.style.left = obj.offsetLeft + step + 'px';
              }, spendTime)
          }
  ```

+ 上移动(缓动返回顶部)

  ```javascript
  /*
  	obj 元素 
  	target 目标距离 
  	callback 回调函数
      spendTime 消耗时间
  */
   function animation(obj, target, spendTime,callback) {
              // 清除定时器 将会只开启一个 定时器
              clearInterval(obj.timer);
              // 物体移动   定时器应用
              obj.timer = setInterval(function () {
                  // 缓动计算公式(step) = (目标值 - 现在的位置) / 10; 
                  var step = (target - window.pageYOffset) / 10;
                  // 判断 step 正负问题
                  step = step > 0 ? Math.ceil(step) : Math.floor(step);
  
                  if (window.pageYOffset == target) {
                      clearInterval(obj.timer);
                      // 回调函数应用
                      if (callback) {
                          callback();
                      }
                  }
                //  obj.style.top = obj.offsetLeft + step + 'px';
                  window.scroll(0,obj.pageYOffset + step );
              }, spendTime)
          }
```
  
  

