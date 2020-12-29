---
title: HTML基础内容详解
tags: HTML
categories: HTML
top: 3
cover: 'https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/HTML.jpg'
abbrlink: 15524
date: 2020-10-14 10:32:26
top_img:
---

```css
基础概念:

	em: em相对于父元素(倍数···)

	rem: rem相对于根元素(···html)
	
	body 字体初始大小: 16px

	html{
		font-size: 62.5%; 配合 rem 使用 14 * 62.5% = 10
	}

	p{
		font-size: 1.4rem  （14px == 14/10 = 1.4rem）  
	}

```



```css
/* 将视窗分为 100 等分 */
img{
	width: 60vw;
	height: 100vh;
}
```



## 默认样式清除:

```css
html{
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    font-size: 62.5%; /* 10px */
}

body{
    margin: 0;
}

*{
    box-sizing: border-box; /* 实际宽度 = width - (border+padding)*/
}

a{
    text-decoration: none; /* 去除超链接下划线 */
    color: #333;
}

ul{
    padding: 0; /* 内边距 */
    margin: 0; /* 外边距 */
    list-style: none;
}

h1,
h2,
h3,
h4,
h5,
h6,
p{
    margin: 0;
    font-weight: normal;
}

img{
    width: 100%;
}

/* 清除浮动 */
.clearfix::after{
    content: "";
    display: block;
    clear: both;
}

```



### `media`媒体查询:

```html
实现自适应

	@media (max-width: xxx px) and (min-width: xxx px) {
 
}

```

![尺寸自适应](https://img-blog.csdnimg.cn/20201018113743254.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

### 盒子相对页面实现垂直居中:

+ 定位(需要知道具体宽高的情况)

  ```html
  <!-- 定义一个盒子 -->
  
  <div class="box"></div>
  ```

  ```css
  <style>
          html,
          body {
              width: 100%;
              height: 100%;
  
          }
  
          body {
              position: relative;
          }
  
          .out-box {
              width: 200px;
              height: 200px;
              background-color: red;
             
              position: absolute;
              left: 50%;
              top: 50%;
              margin-left: -100px;
              margin-top: -100px;
          }
      </style>
  ```

  ```html
  注意: `html` 在过程中发现必不可少,缺少(盒子将会向上偏移盒子高度的一半) 将不能实现垂直居中
  ```

  ![halfBox](https://img-blog.csdnimg.cn/20201018113742183.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

+ 定位(无需具体宽高)

  ```html
   <div class="box"></div>
  ```

  ```css
    <style>
          html,
          body {
              width: 100%;
              height: 100%;
              overflow: hidden;
          }
  
          body {
              position: relative;
          }
  
          .box {
              /* 盒子的宽高不可省略 */
              width: 100px;
              height: 100px;
              background-color: red;
              position: absolute;
  
              right: 0;
              left: 0;
              top: 0;
              bottom: 0;
              margin: auto;
          }
      </style>

  ```
  
  ```css
  
  /* css3属性: 盒子可以让内容撑开 可以没有具体的宽高 */
  
  .box {
              /* 盒子的宽高不可省略 */
              width: 100px;
              height: 100px;
              background-color: red;
              position: absolute;
  			
      		left: 50%;
      		top: 50%;
      		transform:translate(-50%,-50%);
          }
  ```
  
  

+ `flex `布局：

  ```css
  /* 根元素 html 不能少 */ 
  <style>
          html,
          body {
              height: 100%;
          }
  
  
          .box {
              width: 100px;
              height: 100px;
              text-align: center;
              line-height: 100px;
              font-size: 20px;
              background-color: red;
  
          }
  
          body {
              display: flex;
              justify-content: center;
              align-items: center;
          }
      </style>
  ```

  ![垂直居中](https://img-blog.csdnimg.cn/20201018113739779.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)



###  `img `：

```css

<img src="xxx" alt="" title="">

其中alt属性是指图片的替换文本，主要有两个作用:

    ①当根据路径找不到该图片时,作为替换文本出现,不同的浏览器显示形式不一样。

    ②通过alt 可以让搜索引擎知道该图片的内容是什么,因为搜索引擎无法根据图片识别当前图片显示的内容。

其中的title属性的作用为:

	title属性的作用是指当鼠标放在图片上的时候会出现对图片的描述信息

```

### `Web`语义化:

```css

什么是Web语义化:
	
	web语义化包含了html标签语义化和css命名语义化。

	Web 语义化是指使用恰当语义的 html 标签、class类名等内容，让页面具有良好的结构与含义，从而让人和机器都能快速理解网页内容。

```

### html 语义化:

```css
html 语义化标签:

	HTML为网页文档内容提供上下文结构和含义。

html 语义化标签包括 body, article, nav, aside, section, header, footer, hgroup, 还有 h1-h6 address等。


hgroup 元素代表“网页”或“section”的标题，当元素有多个层级时，该元素可以将h1到h6元素放在其内，譬如文章的主标题和副标题组合

article 代表一个在文档，页面或者网站中自成一体的内容，其目的是为了让开发者独立开发或重用。


```

```css
总之，HTML语义化是反对大篇幅使用无语义化的div+span+class，而鼓励使用HTML定义好的语义化标签。
```

### CSS语义化:

```css
CSS语义就是 class 和 ID 命名的语义。

    class 属性作为 HTML 与 CSS 衔接的纽带，其本意是用来描述元素内容的。指用易于理解的名称对 html 标签附加的 class 或 id 命名。

    如果说 HTML 语义化标签是给机器看的，那么 CSS 命名的语义化就是给人看的。良好的 CSS 命名方式减少沟通调试成本，易于理解。

```

###  为什么要语义化？

```css
有利于 SEO

SEO: SEO 也就是 Search Engine Optimization，搜索引擎优化

```



### `display`的属性值:

```css

none 此元素不会被显示

block 此元素将显示为块级元素，此元素前后会带有换行符

inline 默认。此元素会被显示为内联元素，元素前后没有换行符。

inline-block 行内块元素。

inheirt 规定应该从父元素继承 display 属性的值。

```



### 了解并使用 `title` 属性：

![title](https://img-blog.csdnimg.cn/20201023224859920.png#pic_center)



### `span` 元素的基本使用:

```html
	<span> 我是一段文字 </span>

	<span> 我是第二行文字,我们之间有间隙，如何去除间隙？</span>
```

+ `css` 实现价格变更:

  ![del](https://img-blog.csdnimg.cn/20201023232128752.png#pic_center)

+ `del`标签的使用:

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201023232352136.png#pic_center)

```css
span 主要的作用是对普通文本进行归类

```



### `a` 和 `base` 的结合使用:

```html
抽离:

	<base href="https://www.baidu.com" target=“_blank”>


    <div>
		<a href="/img/bd_logo1.png"> 百度一下 </a>
        <a href="/s?wd=vue"> 搜索Vue.js </a>
    </div>

```

### 锚点链接:

```html
使用方式:

	<a href="#要跳转位置标签的 id值 "> Text </a>

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201023235839211.gif#pic_center)



### `URL`:

```css
query 查询

protocol 协议

url: 统一资源定位符

```

### `CSS` 指定字符集:

```css
/* 指定 css 文件的编码 */

@charset "utf-8";

```

### `CSS`引入方式:

```css

<link href="" rel="stylesheet">

<style>
	@import url('css文件的相对路径·········')
</style>

```

### `outline`的使用:

```css
outline: 3px solid red !important; // 可以作为调试技巧 快速了解到布局结构
```

+ 基础布局（使用 `outline`属性快速了解网页布局特性）

```css
 <style>
        .box {
            width: 500px;
            height: 90px;
        }

        .content {
            width: 420px;
            height: 40px;
            float: right;
        }

        div {
            outline: 2px solid red;
        }
    </style>
```

```html
 <div class="box">
        BOX 所占的内容区域
        <div class="content">
            content 所占的内容区域
        </div>
    </div>
```







+ `outline`使用详解

  ![css-outline属性](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/cssline.png)





+ `line-height`详解

  ![line-height](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/linehight.png)

+ `font`:

  ```css
  
  font-variant 斜体  font-weight font-size/line-hieght font-family
  
  font: 30px "宋体" (顺序不可切换)
  
  ```

+ 属性选择器

  ```css
  [title]{
      color: red;
  }
  
  
  <div title="xxx-name">
  	<p title="xxx-p"></p>
  </div>
  ```

  

+ 伪类和伪元素

  ```css
  :target{
      color: red;
  }
  
  作用: 锚点链接点击时发生的效果
  
  ```

  + `:target`的使用效果

    ![target](https://img-blog.csdnimg.cn/2020102418452993.gif#pic_center)

```css
  :disabled {
            color: #f00;
        }


<button disable> 我是有disable的按钮 </button>

<button> 我是没有disable的按钮 </button>

```

![disable与enable的区别](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/disable.png)

<button>BUTTON</button>



+ `a:link` 未访问的超链接
+ `a:hover` 悬停状态
+ `nth:child()` 子类

### `nth:child`详解:

```css

/* n 是自然数 */
nth-child(n){}

/* 2n 偶数位显示效果  2n == even*/
nth-child(2n){} == nth-child(even){}

/* 奇数： odd == 2n+1 */
nth-child(2n+1){} == nth-child(odd){}

/* 负数 代表前几个········*/
nth-child(-n+5){
    /* 前 5 个显示红色 */
    color: red;
}
```

+ `nth-last-child(){}` （倒这数）

+ `nth-of-type(){}`
+ `nth-last-of-type()}{}`

![nth-last-child](https://img-blog.csdnimg.cn/20201024191633699.gif#pic_center)

### `::before 和 ::after`:

```css
xxx::before,
xxx::after{
   content: "";(文字、图片，空)
    /* 其他属性值*/
}
```



###   显示与隐藏的总结

<table>
    <caption> 显示与隐藏的总结</caption>
    <tr>
    	<th>属性</th>
        <th>区别</th>
        <th>用途</th>
    </tr>
    <tr>
    	<td>display</td>
        <td>visibility</td>
        <td>overflow</td>
    </tr>
     <tr>
    	<td>隐藏对象,不保留位置</td>
        <td>隐藏对象,保留位置</td>
        <td>只是隐藏超出大小的部分</td>
    </tr>
     <tr>
    	<td>配合后面的JS做特效,比如下拉菜单,:hover显示与隐藏</td>
        <td>使用较少</td>
        <td>1.清除浮动 2. 保证盒子里面的内容不会超出该盒子范围</td>
    </tr>
</table>



###   文字处理:

```less
1. 先强制一行内显示文本
	white-space: nowrap;
2. 超出的部分隐藏
	overflow: hiddden;
3. 文字用省略号替代超出的部分
	text-overflow: ellipsis;
```



###   弹性盒

```html
弹性容器:
	- 弹性元素就是弹性容器,要使用弹性盒,必须先将元素设置弹性容器
	- 设置弹性容器有两种方式:
		display: flex; 块级弹性容器
		display: inline-flex; 行内弹性容器
弹性元素(弹性项,弹性子元素):
	- 弹性容器中的子元素就是弹性元素
```

```html
弹性元素的属性:
	flex-direction
		- 作用: 用来设置弹性容器的主轴方向
		- 可选值:
			row,主轴时横向的(自左向右 X) 
			row-reverse,主轴是横向的(自右向左排列)
			column,主轴是纵向的(自上向下的排列 Y)
			column-reverse,主轴是纵向的(自下向上排列)

```

```html
flex-wrap
		- 作用: 弹性元素在主轴上是否自动换行
		- 可选值:
			nowrap 默认值
			wrap 自动换行

```

```html
flex-flow: 
	- 作用: 是一个简写属性,可以同时设置 flex-decoration 和 flex-wrap
	- flex-flow: column wrap; <!-- Y 换行 -->
```

+ 主轴的对齐方式

  ```html
  justify-content
  	- 元素在主轴上的对齐方式
  	- 可选值:
  		flex-start 主轴起边
  		flex-end 主轴终边
  		center 主轴的中间
  		space-between 将空白区域平均分配到弹性元素间
  		space-around 将空白空间设置到元素的前后
  		space-evenly 将空白空间设置到元素的一侧
  		stretch 拉伸以使元素充满盒子
  ```

+ 垂轴、辅轴、测轴对齐方式

  ```html
  垂轴、辅轴、测轴对齐方式:
  align-items: 
  	- 可选值:
          flex-start 侧轴起边
          flex-end 侧轴终边
          stretch 拉伸以使元素充满盒子
  align-conetent: 
  	作用: 用来设置辅轴上的空白分布方式
  	flex-start
  ```

  ```html
  当父元素中有空白空间时,需要使用增长的系数,来分配每一个元素的增长大小
  
  flex-grow: 数值
  flex-shrink: 0 
  ```

  

+ 遇见`BFC`

  ```css
  ul>li{内容$}*5
  
  ul{
      border-bottom: 4px solid skyblue；
      // 开启 BFC
      overflow: hidden;
  }
  ul li{
      float: left; // 引起高度塌陷
  }
  ```

  

