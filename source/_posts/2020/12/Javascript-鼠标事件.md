---
title: Javascript-鼠标事件
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 1951
date: 2020-12-11 19:24:54
top_img:
cover:
---

###  mouseenter 和 mousemove 的区别

+ `mouseenter` 鼠标事件

  + 当鼠标移到元素上就会触发 `mouseenter` 事件

  + 类似于 `mousemove`，他们之间的差别是

    +  `mousemove` 鼠标经过自身盒子就会触发,经过子盒子还会触发,`mouseenter` 只会经过自身盒子触发

    + `mouseenter`不会冒泡

  + mouseenter 搭配鼠标离开 `mouseleave` 同样不会冒泡

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201211204151581.gif" title="" alt="缓动动画封装与应用">

  + `css`源码

    ```css
    * {
                margin: 0;
                padding: 0;
            }
    
            .slider-bar {
                position: fixed;
                right: 0;
                top: 100px;
            }
    
            .slider-bar span {
                display: block;
                width: 60px;
                text-align: center;
                color: #fff;
                height: 35px;
                line-height: 35px;
                background-color: red;
    
            }
    
            /* .slider-bar span:hover~.content {
                right: 60px; // css 实现
            } */
    
            .slider-bar .content {
                position: absolute;
                top: 0;
                z-index: -1;
                width: 120px;
                height: 35px;
                line-height: 35px;
                text-align: center;
                background-color: skyblue;
                transition: all .5s
            }
    ```

  + `html`结构

    ```html
     <div class="slider-bar">
            <span> ⬅ </span>
            <!-- 
                ⬅ 左箭头
                ➡ 右箭头
             -->
            <div class="content">
                侧边导航
            </div>
        </div>
    ```

  + `JS`原理分析

    ```javascript
    function animation(obj, target, callbac) {
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
                        if (callbac) {
                            callbac();
                        }
                    }
                    obj.style.left = obj.offsetLeft + step + 'px';
                }, 15)
            }
            /* 
                var move = function () {
                    alert('a');
                } 
            */
            // 箭头函数
            var move = () => {
                alert('a');
            };
    
            var content = document.querySelector('.content');
            var span = document.querySelector('span');
            // 鼠标移入事件
            span.addEventListener('mouseenter', function () {
                animation(content, -60, move);
            });
    
            // 鼠标移出事件
            span.addEventListener('mouseleave', function () {
                animation(content, 0);
            });
    
    ```

    