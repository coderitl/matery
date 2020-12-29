---
title: Javascript-Scroll系列
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 4850
date: 2020-12-11 15:26:56
top_img:
cover:
---

###  Javascript-Scroll系列

|    `scroll`系列属性    |                     作用                     |
| :--------------------: | :------------------------------------------: |
|  `element.scrollTop`   |    返回被卷去的上侧距离,返回数值不带单位     |
|  `element.scrollLeft`  |    返回被卷去的左侧距离,返回数值不带单位     |
| `element.scrollWidth`  | 返回自身的实际宽度,不含边框,返回数值不带单位 |
| `element.scrollHeight` | 返回自身的实际高度,不含边框,返回数值不带单位 |



###  区分

+ 页面被卷去的头部,可以通过 `window.pageYOffset `获得,如果是被卷去的左侧 `window.pageXOffset`
+ 元素被卷去的头部是 `element.scrollTop`，如果是页面被卷去的头部则是 `window.pageYOffset`





###  三大系列总结

| 三大系列大小对比      | 作用                                                         |
| --------------------- | ------------------------------------------------------------ |
| `element.offsetWidth` | 返回自身包括` padding`边框、内容区的宽度、返回数值不带单位   |
| `element.clientWidth` | 返回自身包括` padding ` 内容区的宽度，不包含边框，返回数值不带单位 |
| `element.scrollWidth` | 返回自身实际的宽度、不包含边框，返回数值不带单位             |

###  主要用法

1. offset 系列经常用于获得元素的位置 `offsetLeft offsetTop`
2. client 经常用于获取元素大小` clientWidth clientHeight`
3. scroll 经常用于获取滚动距离 `scrollTop scrollLeft`
4. 注意页面的滚动距离通过 `window.pageXOffset` 获得



###  模块演示

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201211162010294.gif" title="scroll" alt="scroll" width="400">

+ `css`源码

  ```css
   * {
              margin: 0;
              padding: 0;
          }
  
          .box {
              width: 900px;
              margin: 0 auto;
          }
  
          .box div {
              font-size: 30px;
              text-align: center;
              color: #fff;
              font-weight: 700;
              width: 900px;
              height: 800px;
          }
  
          .box div:nth-child(1) {
              background-color: green;
          }
  
          .box div:nth-child(2) {
              background-color: blue;
          }
  
          .box div:nth-child(3) {
              background-color: purple;
          }
  
          .slider-bar {
              display: none;
              position: fixed;
              right: 20px;
              top: 100px;
              width: 150px;
              height: 100px;
  
              background-color: red;
          }
  
          .slider-bar span {
              position: absolute;
              left: 50%;
              top: 50%;
              transform: translate(-50%, -50%);
              text-align: center;
              display: block;
              width: 150px;
              height: 35px;
              color: yellow;
              line-height: 35px;
              cursor: pointer;
          }
  
          .slider-bar span:hover {
              color: #fff;
          }
  ```

+ `html`结构

  ```html
  <div class="slider-bar">
          <span> 返回顶部</span>
      </div>
      <div class="box">
          <div>1</div>
          <div>2</div>
          <div>3</div>
      </div>
  ```

+ `JS`原理分析

  ```javascript
    var _box = document.querySelector('.box');
          // console.log(_divs); nodeList = 3
          var _divs = _box.querySelectorAll('div');
          // 侧边栏 
          var _sliderBar = document.querySelector('.slider-bar');
          // console.log(_divs[1]);
          // 当页面滚动到 .box下第二个 div 显示 slider-bar 
          var _offsetTop = _divs[1].offsetTop;
  
          document.addEventListener('scroll', function () {
              // 获取第二个 div 的高度 包含边框 
              if (window.pageYOffset >= _offsetTop) {
                  _sliderBar.style.display = 'block';
              } else {
                  _sliderBar.style.display = 'none';
              }
          });
  
  
          // 兼容性处理
          function getScroll() {
              return {
                  left: window.pageXOffset || document.documentElement.scrollLeft || document.body.scrollLeft || 0,
                  top: window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0
              };
          }
          getScroll().top;
  ```

  

