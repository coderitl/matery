---
title: Rem的使用
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: css
categories: css
abbrlink: 871
date: 2020-11-26 15:59:46
top_img:
cover:
---

### rem基础
+ `rem`单位:

  > 
  >
  > `rem(root em)`是一个相对单位,类似于`em`，`em`是父元素字体的大小
  >
  > 
  >
  > <font color ="red">不同的是 `rem`的基准的相对于`html` 元素的`字体大小`</font>
  >
  > 
  >
  > `Eg.`
  >
  > + 根元素(`html`) 设置`font-size=12px`，非根元素`width: 2rem`,则换
  >
  >   
  >
  >   成 `px`就是`24px`

  ```css
  
          div {
              /* em 相对于父元素的字体大小来说 */
              font-size: 14px;
          }
  
          p {
              /* 14 * 20 = 280px */
              width: 20em;
              /* 14 * 20 = 280px */
              height: 20em;
              background-color: blue;
          }
  ```

  ```html
   <div>
       <p> a </p>
   </div>
  ```

+ 图解

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/em.png" width="400" alt="加载中···" title="图解em">

  



###  `Less`预处理

+ 基本使用

  + 安装`node`

    + 检测 `node`安装

    + 下载地址: <a href="https://nodejs.org/zh-cn/">https://nodejs.org/zh-cn/</a>

      > `node -v` 输出版本号即为正确安装

  + 安装`Less`

    + `Less`安装

      > `npm install -g less`

    + 监测`Less`安装`

      > `lessc -v`
      >
      > - 输出类似如下信息即为正确安装：
      >
      >   `lessc 3.12.2 (Less Compiler) [JavaScript]`

  + (个人使用感觉比插件方便,推荐)客户端解析工具`Koala`下载

    + `Koala下载链接:`
    + <a href="http://koala-app.com/index-zh.html">http://koala-app.com/index-zh.html</a>

    > 
    >
    > koala是一个前端预处理器语言图形编译工具，支持`Less、Sass、Compass、CoffeeScript，`帮助`web开发者`
    >
    > 
    >
    > 更高效地使用它们进行开发。跨平台运行，完美兼容`windows、linux、mac。`
    >
    > 

+ 快速使用`Less`

  + 变量定义与使用

    ```less
    
    @变量名: 值;
    
    Eg. @color: rgba(255,255,255,.5)
     
    ```

  + `Less`变量使用

    ```less
    body{
    	background: @color;
    }
    ```

  + `Less`<font color="green">可以嵌套书写,并在解析后携带最外层`ID或者类名`,以解决在不同人员之间的因变量名而引起的问题</font>

    <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/Less.png" title="Less使用" alt="图片加载中···">

+ `&`在`Less`中的使用

  + `a:hover`

  + 交集、伪类、为元素选择器

    + 内层选择器前面没有`&`符号,则它被解析为父选择器的后代

      ```less
      Less:
          a{
              color: red;
              :hover{
                  color: blue;
              }
          }
      
      css解析:
          #app a (出现了空格,被解析为父选择器的后代):hover {
            color: blue;
          }
      
      ```

    + 如果有`&`符号,它就解析为父元素自身或父元素的伪类

      ```less
       Less:
      	a{
              color: red;
              &:hover{
                  color: blue;
              }
          }
      
      CSS解析:
          #app a:hover {
              color: blue; // 不在出现空格
          }
      ```

      

+ `Less`运算

  + `+` `-` `*` `/`

    ```less
    Less:
        .header {
            width: 200px + 50;
            height: 200px - 20;
            border: 1px*20 solid red;
            padding: 20px/10;
        }
    
    CSS解析:
        #app .header {
            width: 250px;
            height: 180px;
            border: 20px solid #ff0000;
            padding: 2px;
        }
    ```

  > 
  >
  > <font color="red" size="4">两个数参与运算,如果两个数都有单位,而且不一样的单位,最后的结果以前面的参数的单位为准</font>
  >
  > 

