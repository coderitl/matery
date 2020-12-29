---
title: Animation动画序列
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: css
categories: css
abbrlink: 62402
date: 2020-11-26 22:01:51
top_img:
cover:
---

###  `Animation`动画:

###   波纹效果

![水波效果](https://img-blog.csdnimg.cn/20201126232314783.gif)

+ 实现源码

  ```less
  body {
              background-color: #ccc;
          }
  
          /* 实心圆点 */
          .dotted {
              position: absolute;
              top: 50%;
              left: 50%;
              transform: translate(-50%, -50%);
              width: 8px;
              height: 8px;
              background-color: #09f;
              border-radius: 50%;
          }
  
          .city div[class^="pause"] {
              position: absolute;
              top: 50%;
              left: 50%;
              transform: translate(-50%, -50%);
              width: 8px;
              height: 8px;
              border-radius: 50%;
              box-shadow: 0 0 12px #0099ff;
              animation: scalCircle 1.2s linear infinite;
          }
  
          .city div.pause2 {
              animation-delay: 0.4s;
          }
  
          .city div.pause3 {
              animation-delay: 0.8s;
          }
  
          @keyframes scalCircle {
              0% {}
  
              75% {
                  width: 40px;
                  height: 40px;
                  opacity: 1;
              }
  
              100% {
                  width: 70px;
                  height: 70px;
                  opacity: 0;
              }
          }
  ```

+ `html`结构

  ```html
    <div class="city">
        <div class="dotted"></div>
        <div class="pause1"></div>
        <div class="pause2"></div>
        <div class="pause3"></div>
    </div>
  ```

  

###   爱心缩放

![爱心缩放](https://img-blog.csdnimg.cn/20201127000044412.gif)

+ 爱心实现原理

  + 两个等宽矩形
  + 对矩形的左上、右上进行圆角变化
  + 旋转矩形
  + 定位重合

  ```less
   .box {
              position: absolute;
              width: 220px;
              height: 400px;
              left: 50%;
              top: 50%;
              transform: translate(-50%, -50%);
          }
  
  
          .boxL::before {
              content: "";
              display: inline-block;
              width: 50px;
              height: 80px;
              border-top-left-radius: 50%;
              border-top-right-radius: 50%;
              background-color: red;
              transform: rotate(-45deg);
              animation: love 1.2s linear infinite;
  
          }
  
          .boxL::after {
              position: absolute;
              content: "";
              display: inline-block;
              width: 50px;
              height: 80px;
              left: 22px;
              border-top-left-radius: 50%;
              border-top-right-radius: 50%;
              background-color: red;
              transform: rotate(45deg);
              animation: love 1.2s linear infinite;
          }
  
          @keyframes love {
              0% {}
  
              50% {
                  width: 100px;
                  height: 160px;
                  left: 44px;
              }
  
              100% {
                  width: 50px;
                  height: 80px;
                  left: 22px;
              }
          }
  ```

+ `html`结构

  ```html
   <div class="box">
       <div class="boxL"></div>
   </div>
  ```

  

###  六边形实现背景填充

+ 实现三个等宽矩形
+ 旋转
+ 取消多余边框
+ 暂时未能实现图片填充(后续补充)

###  打字机效果

![CSS3实现打字机动画](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/write.gif)

+ 实现原理

  + 文字属性调整获取动画该进行的步进值(`steps()`)

  + `white-space: norwap;`

  + `overflow: hidden;`

  + 对容器盒子宽度初始为`0`

  + 最终显示文字大小宽度即为实现打字机动画

    ```less
     div {
                width: 0;
                height: 35px;
                line-height: 35px;
                white-space: nowrap;
                font-size: 12px;
                overflow: hidden;
                background-color: #0099ff;
                animation: write 4s steps(7) forwards;
            }
    
            @keyframes write {
                0% {
                    width: 0;
                }
    
                100% {
                    width: 85px;
                }
            }
    ```

  + `html`结构

    ```html
    <div>
       我是打字机效果
    </div>
    ```

###   奔跑的小熊:

![奔跑的小熊](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/bear.gif)

+ 实现原理
  + 先获取一张动画序列图
  + 使用该序列图
  + 设定动画的`steps()`
  + 设定`background-position`

+ 什么是`background-position`？

  > **`background-position`** 为每一个背景图片设置初始位置。 这个位置是相对于由 [`background-origin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-origin) 定义的位置图层的,(引用`MDN`)

+ 怎么理解`background-position`

  > `-200px`（将图片相对容器左移200px，这意味着图片右部分的`100px`内容将出现在容器中）(引用`MDN`)

+ `transform: translate()`不能实现

+ 实现源码

  ```less
   body {
              background-color: #ccc;
          }
  
          div {
              position: absolute;
              top: 50%;
              transform: translate(0, -50%);
              width: 200px;
              height: 100px;
              background: url('img/bear.png') no-repeat;
              animation: bear 1s steps(8) infinite, move 3s forwards;
          }
  
          @keyframes bear {
              0% {
                  background-position: 0 0;
              }
  
              100% {
                  background-position: -1600px 0;
                  transform: translate(-50%);
              }
          }
  
          @keyframes move {
              0% {
                  left: 0;
              }
  
              100% {
                  left: 50%;
              }
          }
  ```

+ `html`结构

  ```html
    <div></div>
  ```





###  3D 转换

`transfom:translate3d(x,y,z)`

> 不可省略 `x,y,z`，没有为 `0`

+ 三维坐标系

  > 三位坐标系其实就是指立体空间,立体空间是由3个轴共同组成

  + X轴: 水平向右 <font color="red" fontWeight="bold">X右边是正值,左边是负值</font>

  + Y轴: 垂直向下 <font color="red">Y下面是正值,上面是负值</font>

  + Z轴: 垂直屏幕 <font color="red">Z外面是正值,往里面是负值</font>

    <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201127111423.png" width="400">

+ 透视(`perspective`)

  + 距离视觉点越近的就在电脑平面成像越大,越远成像越小
  + 透视的单位是像素

+ 透视写在被观察元素的父盒子上面的
  + `d`就是视距,视距就是一个距离人的眼睛到屏幕的距离
  + `z`就是z轴,物体距离屏幕的距离,z轴越大(正值)我们看到的物体就越大 （`可以组略理解为你自己吧电脑搬在自己眼前看东西,Z轴离我们很近,物体自然变大`）

###  3D旋转

+ `transform:rotate3d(x,y,z,deg)`对角线旋转
+ `transform:rotateX(deg)`
+ `transform:rotateY(deg)`

+ `3D效果`
  + `transform-style`
  + `transform-style:preserve-3d` 子元素开启立体空间(父级元素添加)

+ 在没有添加`transform-style`属性下旋转子元素`Y`轴时显示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/rotateY.png" width="400">

+ 添加`transform-style: preserve-3d`后

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/prever-3d.png" width="400" title="只是添加给子盒子的父元素" alt="只是添加给子盒子的父元素">

+ 实现源码

  ```less
  body {
              perspective: 500px;
          }
  
          .box {
              position: relative;
              width: 200px;
              height: 300px;
              margin: 100px auto;
              transition: all 2s;
              transform-style: preserve-3d;
          }
  
          .box:hover {
              transform: rotateY(60deg);
  
          }
  
          .box div {
              position: absolute;
              left: 0;
              top: 0;
              width: 100%;
              height: 100%;
              background-color: skyblue;
          }
  
          .box div:last-child {
              background-color: purple;
              transform: rotateX(60deg);
          }
  ```

+ `html`结构

  ```html
   <div class="box">
          <div></div>
          <div></div>
      </div>
  ```



###  圆圈3D旋转

<img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/circle.gif" alt="圆圈翻转" title="圆圈反转">

+ 实现原理
  + 两个`div`添加圆角属性
  + 对子元素的父盒子添加`transform-style:preserve-3d;  perspective: 500px;`
  + 对父元素添加`hover`效果

+ 实现源码

  ```less
   body {
              perspective: 500px;
          }
  
          .box {
              position: relative;
              text-align: center;
              color: #fff;
              width: 300px;
              height: 300px;
              line-height: 300px;
              margin: 100px auto;
              transition: all .4s;
  
              transform-style: preserve-3d;
          }
  
          .box:hover {
              transform: rotateY(180deg);
          }
  
          .box div {
              position: absolute;
              left: 0;
              top: 0;
              width: 100%;
              height: 100%;
              text-align: center;
              border-radius: 50%;
              background-color: skyblue;
              box-shadow: 0 0 12px rgba(0, 0, 0, .5);
          }
  
          .box div:last-child {
              background-color: purple;
              transform: rotateY(180deg);
          }
  ```

+ `html`结构

  ```html
  <div class="box">
          <div>人生苦短,我学编程</div>
          <div>我在哔哩哔哩所学总结</div>
      </div>
  ```

  

###  旋转木马

+ 实现原理
  + 定位 + 3D旋转
  + 旋转度数 = 360 / 图片数量
  + 添加动画
  + 景深效果
  + `transform-style: preserve-3d`添加给子元素的父级



