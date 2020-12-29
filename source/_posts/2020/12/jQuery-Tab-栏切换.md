---
title: jQuery-Tab-栏切换
tags: jQuery
categories: jQuery
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
abbrlink: 51815
date: 2020-12-12 19:24:06
top_img:
cover:
---



###  Tab-栏切换实战

+ 效果演示
<img src="https://img-blog.csdnimg.cn/20201217180209666.gif" alt="jQuery-Tab栏切换" title="jQuery-Tab栏切换">


+ `css`源码（注意权重问题）

  ```css
   * {
              margin: 0;
              padding: 0;
          }
  
          .box {
              width: 960px;
              height: 100%;
              margin: 100px auto;
          }
  
          .box .tab-item {}
  
          .tab-item ul {
              list-style: none;
              overflow: hidden;
              width: 100%;
              border-bottom: 4px solid rgba(0, 0, 0, .5);
              margin-bottom: 3px;
          }
  
          .tab-item ul li {
              float: left;
              width: 140px;
              height: 35px;
              color: #bfc;
              text-align: center;
              line-height: 35px;
              background-color: pink;
              margin-right: 10px;
              cursor: pointer;
              transition: all .5s;
          }
  
          .content {
              position: relative;
          }
  
          .content .item {
              position: absolute;
              width: 100%;
              height: 200px;
              display: none;
              background-color: skyblue;
          }
  
          .tab-item ul .current {
              width: 140px;
              height: 35px;
              color: red;
              background-color: #09f;
          }
  ```

+ `html`结构

  ```html
      <div class="box">
          <div class="tab-item">
              <ul>
                  <li class="current">测试文本 1</li>
                  <li>测试文本 2</li>
                  <li>测试文本 3</li>
                  <li>测试文本 4</li>
                  <li>测试文本 5</li>
              </ul>
          </div>
          <div class="content">
              <div class="item" style="display: block;"> 测试文本 1</div>
              <div class="item"> 测试文本 2</div>
              <div class="item"> 测试文本 3</div>
              <div class="item"> 测试文本 4</div>
              <div class="item"> 测试文本 5</div>
          </div>
      </div>
  ```

+ `JS`原理分析

  ```javascript
          $(function () {
              $('.tab-item>ul>li').click(function () {
                  // li 点击谁谁获取该类 他的兄弟移除该类
                  $(this).addClass('current').siblings().removeClass('current');
                  // 获取点击元素的 index 
                  var index = $(this).index();
                  // item 对应的 index 显示
                  $('.content>.item').eq(index).show().siblings().hide();
              })
          })
  ```

  