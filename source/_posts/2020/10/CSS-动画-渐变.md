---
title: CSS-动画-渐变
date: 2020-10-29 15:57:53
tags: HTML
categories: 
- HTML
top_img:
cover: https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/ann.jpg
---

###  `CSS 动画`   - `animation`：

> ``animation`` `属性用来指定一组或多组动画，每组之间用逗号相隔。`

> ```scss
> animation: 3s ease-in 1s infinite reverse both running slidein;
> 
> animation: 3s linear 1s infinite running slidein;
> 
> animation: 3s linear 1s infinite alternate slidein;
> 
> animation: .5s linear 1s infinite alternate slidein;
> ```



###   `综合运用 animation`：

> + 定义动画
>
> ```scss
>   -webkit-animation: carousel 8s infinite linear;
> 
> 					// 动画名称 时间  xxx  方式
> ```



> + 使用动画(替代轮播图效果)
>
> ```scss
> @-webkit-keyframes carousel{
>     0%{
>         background-image: url("../access/img/top-banner/banner01.jpg");
>     }
>     50%{
>          background-image: url("../access/img/top-banner/banner02.png");
>     }
>     100%{
>          background-image: url("../access/img/top-banner/banner03.png");
>     }
> }
> ```





###  `CSS 颜色渐变`:

> 
>
> ```scss
> 
> * 渐变轴为45度，从蓝色渐变到红色 */
> 
> linear-gradient(45deg, blue, red);
> 
> /* 从右下到左上、从蓝色渐变到红色 */
> linear-gradient(to left top, blue, red);
> 
> /* 从下到上，从蓝色开始渐变、到高度40%位置是绿色渐变开始、最后以红色结束 */
> linear-gradient(0deg, blue, green 40%, red);
> ```
>
> + 

+ 上到下渐变

  > ```scss
  > background: linear-gradient(#e66465, #9198e5);
  > ```
  >
  > + 效果图
  >
  >   ![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/linear01.png)

+ 左到右渐变

  > ```css
  > background: linear-gradient(0.25turn, #3f87a6, #ebf8e1, #f69d3c);
  > ```
  >
  > + 效果图
  >
  >   ![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/linear02.png)

+ 混色渐变

  > ```scss
  > background: linear-gradient(217deg, rgba(255,0,0,.8), rgba(255,0,0,0) 70.71%),
  >             linear-gradient(127deg, rgba(0,255,0,.8), rgba(0,255,0,0) 70.71%),
  >             linear-gradient(336deg, rgba(0,0,255,.8), rgba(0,0,255,0) 70.71%);
  > ```
  >
  > + 效果图
  >
  >   ![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/linear03.png)





###  `理解 linear-gradient`:

+ 起点方向

  ![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/linear-all.png)

> + 方向(`···deg`)
>
>   ![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/direcation.png)
>
> ```scss
> linear-gradient((方向)角度,颜色值1，颜色值2，····);
> ```





###  `filter`(`滤镜--> 高斯模糊`)：

> ```scss
> 
>         .box {
>             width: 100%;
>             height: 50px;
>             position: absolute;
>             top: 0;
>             left: 0;
>             right: 0;
>         }
> 
>         .blue {
>             position: absolute;
>             background-color: blue;
>             left: 0;
>             right: 0;
>             bottom: 0;
>             top: 0;
> 			// blur(值越大模糊程度越高)
>             filter: blur(8px);
>         }
> ```
>
> ```html
>   <div class="box">
>         <div class="blue"></div>
>     </div>
> ```
>
> + 效果图
>
>   <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/fliter.png" style="zoom:80%;" />

