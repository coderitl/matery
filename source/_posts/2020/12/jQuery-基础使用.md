---
title: jQuery-基础使用
tags:
  - jQuery
categories:
  - jQuery
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
abbrlink: 17726
date: 2020-12-12 19:24:06
top_img:
cover:
---

###  jQuery-基础使用

+ 下载

  

+ 引用

+ 输出`Hello world`

```javascript
// 入口函数
$(function () {
            alert('Hello World');
    		// 打印顶级对象 $
            console.dir($);
            console.dir(jQuery);
        })
```

###  DOM 对象和 jQuery 对象

<img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/dom.png" alt="DOM和jQuery对象" title="DOM和jQuery对象">

```javascript
 		// DOM 对象和 jQuery 对象 获取
            console.log('------------ DOM 对象 ------------');
            var _div = document.querySelector('div');
            console.log(_div);

            console.log('------------ jQuery 对象 ------------');
            var $div = $('div');
            console.log($div);
```

###  DOM 和 jQuery 之间的转换

###  DOM 转换 jQuery 对象

+ `html`结构

  ```html
    <div>
  
    </div>
  ```

+ `JS`原理分析

  ```javascript
     var _div = document.querySelector('div');
      console.log(_div);
     // 链式操作
      console.log($(_div).css({ width: 600, height: 200, background: 'blue' }));
  ```

+ 效果展示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/$Img.png" width="400">

#### jQuery 转换 DOM 对象

```javascript
jQuery 转换 DOM 对象:
                    $('获取的元素')[index] index 是索引号
                    $('获取的元素').get(index) index是索引号
```



###  jQuery基本和层级选择器

|    名称    |       用法        |
| :--------: | :---------------: |
| ID 选择器  |     `$("id")`     |
| 全选选择器 |     `$("*")`      |
|  类选择器  |   `$(".class")`   |
| 并集选择器 | `$("div,p,span")` |
| 交集选择器 | `$("li.current")` |
| 标签选择器 |    `$("div")`     |

+ 元素获取`隐式迭代`

  ```html
   <ul>
              <li></li>
              <li></li>
              <li></li>
          </ul>
  ```

+ `JS`原理

  ```javascript
  console.log($("ul li"));
  ```

+ 效果展示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/$li.png">

### jQuery 选择器

| 语法         | 用法                | 描述 |
| ------------ | ------------------- | ---- |
| `:first`     | `$("li:first")`     |      |
| `:last`      | `$("li:last")`      |      |
| `:eq(index)` | `$("li:eq(index)")` |      |
| `:odd`       | `$("li:odd")`       |      |
| `:even`      | `$("li:even")`      |      |



###  jQuery 的筛选方法(重点)

|                     语法                      |                         用法                          |                             说明                             |
| :-------------------------------------------: | :---------------------------------------------------: | :----------------------------------------------------------: |
|                   parent()                    |      <font color="red">`$("li").parent()`</font>      |                           查找父级                           |
|              children(selector)               |                                                       |                                                              |
|                find(selector)                 |     <font color="red">`$("ul").find("li")`</font>     |                相当于 `$("ul li")`后代选择器                 |
| <font color="red">`siblings(selector)`</font> | <font color="red">`$(".first").siblings("li")`</font> |                   查找兄弟节点,不包括本身                    |
|                nextAll([expr])                |                                                       |                                                              |
|     <font color="red">`eq(index)`</font>      |     <font color="red">`$("li").eq(index)`</font>      | <font color="red">`相当于 $("li:eq(2)"),index 从 0 开始`</font> |
|                                               |                                                       |                                                              |

 ###  新浪下拉菜单(jQuery实现)

+ 效果演示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/ $xl.gif" width="400" alt="鼠标移入移出事件" title="鼠标移入移出事件">

+ `html`结构

  ```html
  <div class="box">
          <ul class="ul">
              <li>
                  <a href="#"> 客户服务 </a>
                  <ul>
                      <li> <a href="#"> 联系客服 </a></li>
                      <li> <a href="#"> 帮助中心 </a></li>
                      <li> <a href="#"> 知识产权保护</a> </li>
                      <li> <a href="#"> 规则中心 </a></li>
                  </ul>
              </li>
              
              ···
      </ul>
  </div>
  ```

  

+ `JS`原理分析

  ```javascript
  $(function () {
              $(".ul>li").mouseover(function () {
                  $(this).children("ul").show();
              });
              $(".ul>li").mouseout(function () {
                  $(this).children("ul").hide();
              })
          })
  ```

  

###  排它思想

+ 效果演示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/ $mouseover.gif" alt="排它思想" title="排它思想" width="600">

+ `html`结构

  ```html
   <div class="box">
          <ul>
              <li>1</li>
              <li>2</li>
              <li>3</li>
              <li>4</li>
              <li>5</li>
              <li>6</li>
          </ul>
      </div>
  ```

+ `JS`原理分析

  ```javascript
   $(function () {
       		// 获取 li 的鼠标移入事件
              $(".box>ul>li").mouseover(function () {
                  // 当前 li 的 背景色改为红色 其他兄弟的背景颜色不变
                  $(this).css('backgroundColor', 'red').siblings("li").css("backgroundColor", "");
              })
          });
  ```

  

###  操作 CSS 方法

+ 预编译类

  ```css
  .current {
              background-color: pink;
              transform: rotate(360deg);
          }
  ```

+ 添加类

  ```javascript
    // 普通点击事件 修改类样式
      $('div').click(function () {
          $(this).css('backgroundColor', 'skyblue');
      }) 
   // 添加已经编辑好的类样式
      $('div').click(function () {
          $(this).addClass('current');
      })
  ```

+ 切换类

  ```javascript
  
      // 切换类
      $('div').click(function () {
          $(this).toggleClass('current');
      })
  
  ```

+ 删除类

  ```javascript
  // 删除类
      $('div').click(function () {
          $(this).removeClass('bg');
      })
  ```

