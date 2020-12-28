---
title: Emmet语法和表格的使用
date: 2020-10-24 20:33:09
tags: 
- HTML
categories: 
- "HTML"
top: 6
top_img:
cover: https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/Emmet.png
---

### `Emmet` 语法使用:

+ `vscode`快速生成 `html5`代码模板

  ```html
  ! 感叹号
  
  html:5
  ```

+ 子代

  ```html
  语法: div>p>h1
  
  结果:
  
      <div>
        <p>
            <h1>
            </h1>
        </p>
    </div>
  
  ```

+ 兄弟

  ```html
  语法: div+p+span+a
  
  结果:
      <div></div>
      <span></span>
      <p></p>
      <a href=""></a>
  
  ```

+ 兄弟和子代同时使用

  ```html
  
  语法: div>h2+a+p>span
  
  结果:
  	<div>
          <h2></h2>
          <a href=""></a>
          <p>
  			<span></span>
  		</p>
  	</div>
  
  ```

  

+ 综合使用

  ```html
  
  	语法: div#main>div.box+p.p1+span.title^div#rooter>div.box2
  
  	结果:
      <div id="main">
          <div class="box"></div>
          <p class="p1"></p>
          <span class="title"></span>
      </div>
      <div id="rooter">
          <div class="box2"></div>
      </div>
  
  ```

+ 内容

  ```html
  语法: div#main.box{我是内容}
  
  结果:
  
  	   <div id="main" class="box">我是内容</div>
  
  ```

+ 内容中有数字

  ```html
  语法: div#main.box{我是内容$}*5
  
  结果:
  	
   <div id="main" class="box">我是内容1</div>
   <div id="main" class="box">我是内容2</div>
   <div id="main" class="box">我是内容3</div>
   <div id="main" class="box">我是内容4</div>
   <div id="main" class="box">我是内容5</div>
  
  ```

+ 隐式标签

  ```css
  语法: .box,#main················
  ```

+ `li`

  ```html
  语法:  ul>li.item${我是内容$}*5
  
  结果: 
  	<ul>
          <li class="item1">我是内容1</li>
          <li class="item2">我是内容2</li>
          <li class="item3">我是内容3</li>
          <li class="item4">我是内容4</li>
          <li class="item5">我是内容5</li>
      </ul>
  ```

+ `table`:

  ```html
  
  ```

  

+ `css`的 `Emmet`:

  ```css
  语法: .box{
      		w200+h200+m20+p30
  		  }
  
  结果:
  
      .box{
              width: 200px;
              height: 200px;
              margin: 20px;
              padding: 30px;
          }
  
  ```

+ `margin` 和 `padding`的上右下左:

  ```css
  margin: 上 右 下 左
  
  语法: m20-30-45-67 /p20-30-45-67
  
  结果:  
  
  	margin: 20px 30px 45px 67px;
  
  	padding: 20px 30px 45px 67px;
  		
  ```

  

+ 字体

  ```css
  语法:
      fw
      fz
      lh90px
  
  结果:
      font-weight: 20;
      font-size: 20px;
  	line-height: 90px;
  ```

+ 表格

  ```scss
  tr 表中的行
  
  td 行中的单元格
  
  
  table 的属性:
  	
  	border 边框的宽度
  	cellpadding 单元格内部的间距
  	cellspacing 单元格之间的间距
      width 表格的宽度
      align 表格的水平对齐方式 (let、center、right)
  
  ```

+ `tr`的属性

  ```css
  
  valign 单元格得垂直对齐方式 top、middle、bottom、baseline
  
  align 单元格得水平对齐方式 left、center、right
  
  ```

  

+ 表格边框合并

  ```css
  border-collapse: collapse;
  ```

  + 合并后的显示

    ![border-collapse-collapse](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/table.png)

+ 表格中的其他元素

  ```css
  tbody 表格的主体
  caption 标题栏
  thead 
  ```

  ![caption](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/caption.png)

  ```html
    <table>
              <caption> 内容记录排行 </caption>
              <tr>
                  <td>内容1</td>
                  <td>内容2</td>
                  <td>内容3</td>
                  <td>内容4</td>
                  <td>内容5</td>
              </tr>
    </table>
  ```

### 一张完整的表格:（`border-collapse: collapse`）

![完整的表格](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/tableContent.png)

### 表格单元格的合并:

```css
语法: table>(tr>td{单元格$}*5)*3

结果: xxxx··············
```



### 合并的分析:



+ 浏览器显示结果(分析)

  ![合并后在浏览器按下f12](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/collspan.png)

+ 通过开发工具者分析

  ![分析合并的原理](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/ChromeTd.png)

+ 请尝试其他

  ![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/redTd.png)



### 课程表案例练习:

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        table {
            width: 680px;
            margin: 20px auto;
            line-height: 49px;
            text-align: center;
            border-collapse: collapse; /* *************** */
            border: 1px solid skyblue;
        }

    th,
    tr,
    td {
        border: 1px solid skyblue;
    }
    
    th {
        height: 30px;
        line-height: 30px;
    }
    
    caption {
        border: 1px solid skyblue;
        border-bottom-width: 0;
        font-weight: bold;
        font-size: 20px;
        color: rgb(39, 37, 37);
    }
</style>

</head>

<body>
    <div class="box">
        <table>
            <caption> 课程表 </caption>
            <tr>
                <th></th>
                <th>星期一</th>
                <th>星期二</th>
                <th>星期三</th>
                <th>星期四</th>
                <th>星期五</th>
            </tr>
            <tr>
                <td rowspan="4">上午</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
            <tr>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
            <tr>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
            <tr>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
            <tr>
                <td rowspan="4">下午</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
            <tr>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
            <tr>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
            <tr>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
            <tr>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
            <tr>
                <td rowspan="2">晚自习</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
            <tr>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
                <td>生物</td>
            </tr>
        </table>
    </div>
</body>

</html>





