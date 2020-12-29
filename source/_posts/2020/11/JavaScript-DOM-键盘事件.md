---
title: JavaScript-DOM-键盘事件
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 13060
date: 2020-11-29 21:09:37
top_img:
cover:
---

###  键盘事件

|   键盘事件   |                           触发条件                           |
| :----------: | :----------------------------------------------------------: |
|  `onkeyup`   |                    某个键盘按键松开时触发                    |
| `onleydown`  |                   某个键盘按键被按下时触发                   |
| `onkeypress` | 某个键盘按键被按下时触发 **但是它不识别功能键 `ctrl shift` 区分大小写** |

+ 执行顺序

  `keydown - keypress - keyup`

```javascript
// 获取按下的键的 keyCode
        document.addEventListener('keydown', function (e) {
            console.log(e);
        });

        // 获取按下的键的 keyCode
        document.addEventListener('keyup', function (e) {
            console.log(e);
        });

        // 获取按下的键的 keyCode
        document.addEventListener('keypress', function (e) {
            console.log(e);
        });

```

+ 模拟京东

  ```javascript
  
          // 获取按下的键的 keyCode s===83 
          document.addEventListener('keyup', function (e) {
              if (e.keyCode === 83) {
                  input.focus();
              }
          });
  ```

  

###  案例

+ `css`源

  ```less
   span {
              opacity: 0;
              margin: 10px 0 0 10px;
              display: block;
              width: 163px;
              height: 30px;
              font-size: 16px;
              line-height: 30px;
              border: 1px solid #0099ff;
              transition: all .5s;
              overflow: hidden;
          }
  
          label {
              display: block;
              width: 300px;
              height: 100px;
              border: 5px solid #000;
              margin: 100px auto;
          }
  
          input {
              margin: 0 0 0 10px;
          }
  ```

+ `html`结构

  ```html
   <label for="">
              <span> </span>
              <input type="text" value="请输入">
          </label>
  
  ```

+ `JS`原理分析

  ```javascript
  // 获取 input 
          var input = document.querySelector('input');
          var span = document.querySelector('span');
          input.onclick = function () {
              input.value = '';
              input.addEventListener('keyup', function () {
                  if (input.value.length > 0) {
                      span.style.opacity = '1';
                      span.innerHTML = input.value;
                  } else {
                      span.style.opacity = '0';
                  }
              });
          }
  ```

  