---
title: CSS-盒子模型
date: 2020-10-26 11:41:24
tags: HTML
categories: 
- HTML
top_img: 
cover: https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/boxS.png
---

###  盒子模型:

```html
width

height

margin

padding

border

content
```

![盒子模型](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/box.png)

### 上下 `margin` 传递:

```css
<style>
        .box1 {
            width: 200px;
            height: 200px;
            background-color: #f00;
        }

        .box {
            width: 200px;
            height: 200px;
            background-color: green;
            /*  overflow: hidden; 将会触发 BFC */
          	overflow: hidden;
        }

        .inner {
            width: 100px;
            height: 100px;
           
            margin-top: 20px; 
            
            background-color: yellow;
        }
    </style>
```

```html
 	<!-- 对比 -->
    <div class="box1"></div>

    <!-- margin-top 传递 -->
    <div class="box">
        <div class="inner"></div>
    </div>

```

+ 基础效果（`绿色盒子为 inner`）

  ![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/margintop.png)

+ 对 `inner`盒子添加 `margin-top`效果

  ![margin-top](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/topmargin.png)

  

+ 什么是 `BFC`：

  > 
  >
  > **块格式化上下文（Block Formatting Context，BFC）** 是Web页面的可视CSS渲染的一部分，是块盒子的布局过程发生的区域，也是浮动元
  >
  > 素与其他元素交互的区域。
  >
  > 

+ 如何触发 `BFC`：

  > + 浮动可以触发
  > + 设置一个元素的 overflow 为非 visible
  >   + hidden
  >   + auto
  >   + scroll

+ 添加`overflow: hidden`

  ![overflow-hidden](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/overflow.png)

+ 在不了解 `BFC`可以使用 `padding`加在父元素身上（存在弊端）

  ![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/padding-overflow.png)

### `box-shadow`：

```css


    /* x偏移量 | y偏移量 | 阴影模糊半径 | 阴影颜色 */
    box-shadow: 10px 5px 5px black;

    /* x偏移量 | y偏移量 | 阴影模糊半径 | 阴影扩散半径 | 阴影颜色 */
    box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);

  
```

+ `box-shadow`：

  ![box-shadow](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/box-shadow.png)

### `text-shadow`:

```css

offset-x | offset-y | blur-radius(模糊) | color 
   
text-shadow:2px 2px 3px #FF0000;

```

+ 霓虹灯文字效果

  ![霓虹灯文字效果](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/helloworld.png)



### 盒子尺寸`box-sizing`：

```css

默认内容盒子:
	
	content-box： 含义是设置宽度和高度时只是指定内容的宽高

	border-box: 含义是设置宽度和高度时是 内容 + 内边距 + 边框的宽度


	box-sizing: border-box;
```

+ `content-box与border-box的差异`:

  ![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/cintent-border.png)



### `margin: 0 auto`：

```css
margin: 0 auto;

auto == margin-left / margin-right

水平方向的父元素的宽度是 auto

```



### `css Sprite`(精灵图)：

![sprite](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/sprite.png)

+ 京东精灵图

  ![京东精灵图](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/SpriteImg.png)

+ 多快好省练习

```css
<style>
        /* reset */
        ul {
            list-style: none;
            margin: 0;
            padding: 0;
        }

        a,
        p,
        h5,
        body {
            margin: 0;
            padding: 0;
        }

        /* 具体样式 */
        ul li,
        h5,
        p {
            display: inline-block;
        }

        li {
            margin-left: 12px;
            margin-right: 18px;
            height: 42px;
            line-height: 42px;
            font-size: 18px;
            font-weight: 700;
        }

        h5 {
            width: 36px;
            height: 42px;
            text-indent: -999px; /* 新内容 ················ */
            background-image: url(SpriteImg.png);
        }

        .duo {
            background-position: 0 -192px;

        }

        .kuai {
            background-position: -41px -192px;
        }

        .hao {
            background-position: -82px -192px;
        }

        .sheng {
            background-position: -123px -192px;
        }

        .server {
            margin: 150px auto;
            width: 960px;
        }
```

```html
 <div class="server">
        <div>
            <ul>
                <li>
                    <h5 class="duo">多</h5>
                    <p>品类齐全,轻松购物</p>
                </li>
                <li>
                    <h5 class="kuai">快</h5>
                    <p>多仓直发,急速配送</p>
                </li>
                <li>
                    <h5 class="hao">好</h5>
                    <p>正品行货,精致服务</p>
                </li>
                <li>
                    <h5 class="sheng">省</h5>
                    <p>天天低价,畅叙无忧</p>
                </li>
            </ul>
        </div>
    </div>
```

###  `background-attachment`：

```css
background-attachment:

	属性值: local、fixed、scroll
```



### `img`和`background-image`的区别:

```css
 table {
            width: 600px;
            text-align: center;
            line-height: 35px;
            margin: 150px auto;
            /* 合并边框对于表格很重要 */
             border-collapse: collapse;
        }
	th,
    tr,
    td {
        margin: 0;
        padding: 0;
        border: 1px solid skyblue;
    }
```
<table align="center">
        <tr>
            <th></th>
            <th>img</th>
            <th>background-image</th>
        </tr>
        <tr>
            <td> 性质</td>
            <td> HTML元素</td>
            <td> CSS样式</td>
        </tr>
        <tr>
            <td> 图片是否占用空间 </td>
            <td> √ </td>
            <td> × </td>
        </tr>
        <tr>
            <td> 浏览器右键直接查看地址</td>
            <td> √ </td>
            <td> × </td>
        </tr>
        <tr>
            <td> 支持 CSS Sprite </td>
            <td> × </td>
            <td> √ </td>
        </tr>
        <tr>
            <td> 更有可能被搜索引擎收录 </td>
            <td> √ (结合alt 属性)</td>
            <td> × </td>
        </tr>
        <tr>
            <td> 加载书顺序 </td>
            <td> 优先加载 </td>
            <td> 等加载完HTML元素后再加载</td>
        </tr>
    </table>


