---
title: JavaScript-DOM操作
password: ''
tags: JavaScript
categories: javascript
abbrlink: 41787
date: 2020-11-27 15:12:42
top_img:
cover:
---



###  JavaScript-DOM 操作:

+ 什么是`DOM`

  > 文档对象模型(`Document Object Model，简称DOM`)是`W3C`组织推荐的处理可扩展标记语言

####  元素获取:

​		<img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/getElementByTagname.png" width="600" alt="DOM元素获取" title="DOM元素获取">

+ 根据元素`ID`获取元素 `document.getElementById()`

  ```javascript
  var Obox = document.getElementById('box');
  console.log(Obox);
  ```

+ 根据标签名称获取元素(伪数组)`document.getElementsByTagName()`

  ```javascript
   var Olis = document.getElementsByTagName('li');
   console.log(Olis);
  ```

+ <font color="red" fontWeight="bold">  获取某个元素(父元素)内部所有指定标签名的子元素`element.getElementsByTagName('标签名');`</font>

+ `html`结构

  ```html
   <div id="box">
          <ul id="Oul" class="Ou1">
              <li><a href="#"> ID-01-UL</a></li>
              <li><a href="#"> ID-01-UL</a></li>
              <li><a href="#"> ID-01-UL</a></li>
              <li><a href="#"> ID-01-UL</a></li>
              <li><a href="#"> ID-01-UL</a></li>
          </ul>
          <ul id="Ou2" class="Ou2">
              <li><a href="#"> CLASS-02-UL</a></li>
              <li><a href="#"> CLASS-02-UL</a></li>
              <li><a href="#"> CLASS-02-UL</a></li>
              <li><a href="#"> CLASS-02-UL</a></li>
              <li><a href="#"> CLASS-02-UL</a></li>
          </ul>
      </div>
  ```

+ `JS`获取元素

  ```javascript
  相同结果:
  	+ 根据 ID
  	// 获取某个元素(父元素)内部所有指定标签名的子元素
          // element.getElementsByTagName('标签名');
          console.log('------------ 使用 ID 获取 ------------');
          var _Oul = document.getElementById('Ou2');
          var _Olis = _Oul.getElementsByTagName('li');
          console.log(_Olis);
  
  	+ 根据 ID 或者 类名 获取
          // 使用 querySelector()
          console.log('------------  querySelector || querySelectorAll ------------');
          var _Ou2_ = document.querySelector('.Ou2');
          console.log(_Ou2_);
          var _Olis_ = document.querySelectorAll('.Ou2>li');
          console.log(_Olis_);
  ```

  

<img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/getID-querySelector.png" alt="页面中ol>li的获取" title="页面中ol>li的获取">



###  获取特殊元素

+ `body`

  ```javascript
   var bodyElement = document.body;
   console.log(bodyElement);
  ```

+ `html`

  ```javascript
  var htmlElement = document.documentElement;
  console.log(htmlElement);
  ```

+ 输出展示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/getBody-Html.png" alt="body和html特殊元素获取" title="body和html特殊元素获取">
  
   

###  事件三要素

+ 事件三要素
  + 事件源
  + 事件类型
  + 事件处理程序

```javascript

// 获取事件源
var btn = document.getElementById('btn');
// 事件类型
btn.addEventListener('click', function () {
    // 事件处理程序
    alert('按钮发生了点击');
    console.log('按钮发生了点击!');
})
```

+ 事件效果展示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/alert.png">

+ 点击事件另一种写法

  ```javascript
    var btn = document.getElementById('btn');
          btn.onclick = function () {
              console.log('另一种点击事件写法···');
          }
  ```

  

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/click.png" alt="onclick()" title="onclick">

###  常见的鼠标事件

|   鼠标事件    |     触发条件     |
| :-----------: | :--------------: |
|   `onclick`   | 鼠标点击左键触发 |
| `onmouseover` |   鼠标经过触发   |
| `onmouseout`  |   鼠标离开触发   |
|   `onfocus`   | 获得鼠标焦点触发 |
|   `onblur`    | 失去鼠标焦点触发 |
| `onmousemove` |   鼠标移动触发   |
|  `onmouseup`  |   鼠标弹起触发   |
| `onmousedown` |   鼠标按下触发   |

###   操作元素--修改元素内容

```javascript

// 修改按钮的文本显示信息
var _btn = document.getElementById("btn");
_btn.addEventListener('click', function () {
    _btn.innerHTML = "点击发生改变的文字信息";
})

```

+ 效果展示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/btnClick.png" alt="innerHTML" title="innerHTML">

+ `innerText`与`innerHTML`的区别

  + `innerText`

    > + 不识别标签
    > + 去除空格和换行

  + `innerHTML`

    > + 识别标签
    > + 保留空格和换行

###  元素属性的修改

+ `src`

+ `href`

+ `id`

+ `alt`

+ `title`

  ```javascript
  // 修改按钮的文本显示信息
          var _baidu = document.getElementById("baidu");
          var _taobao = document.getElementById("taobao");
          var _a = document.querySelector('a');
          _baidu.addEventListener('click', function () {
              _a.href = 'https://www.baidu.com';
              _a.innerHTML = _a.href;
          })
          _taobao.addEventListener('click', function () {
              _a.href = 'https://ai.taobao.com/';
              _a.innerHTML = _a.href;
          })
  
  ```

+ 效果显示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/_aHref.gif" alt="JS点击修改链接属性" title="JS点击修改链接属性">

###  表单元素的`DOM`操作

> 
>
> `type、value、checked、selected、disabled`
>
> `type` 密码框明文与暗文案例
>
> 



###  `JS`修改元素的大小,颜色,位置等样式

> + `JS`里面的样式采用驼峰命名法
> + `JS`修改`style`样式修改,产生的是行内样式,`CSS`权重比较高

###  `JS`修改类名

+ 修改的类

  ```less
     .box {
         width: 10px;
         height: 10px;
         border: 10px solid red;
          }
  
      .changeBox {
          width: 100px;
          height: 100px;
          background-color: purple;
          margin: 100px auto;
      }
  ```

  

+ `html`结构

  ```html
  <div class="box"></div>
  ```

+ `JS`动态修改 添加类

  ```javascript
  	var _box = document.querySelector('.box');
      + 方法一: 
          // 添加 onmouseover 将失效，去除 on 即为鼠标移入监听正确
          _box.addEventListener('mouseover', function () {
              _box.className = 'changeBox';
          })
      + 方法二:
          // 必须添加 on
          _box.onmouseover = function () {
              _box.className = 'changeBox'; // 多类名添加空格
          };
  ```

###   案例练习

<img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/formClassname.png" alt="表单验证" title="表单验证"> 

+ 实现原理分析
  + 准本两个类
    + `wrong`
    + `right`
  + 通过对`onblur`事件判断
    + 正确添加 `right`类
    + 否则添加 `wrong`类（`element.className`）
    + 动态修改`innerHTML`信息

###   排它思想

![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/li.png)

+ `CSS实现源码`

  ```less
   body {
              background-color: #cccccc;
          }
  
          .box ul {
              list-style: none;
              width: 100px;
              margin: 200px auto;
          }
  
          .box ul li {
              float: left;
              width: 8px;
              height: 8px;
              margin-right: 10px;
              border-radius: 50%;
              cursor: pointer;
              border: 1px solid #000;
              background-color: #fff;
          }
  ```

+ `html`结构

  ```html
  <div class="box">
          <ul class="uL">
              <li></li>
              <li></li>
              <li></li>
              <li></li>
              <li></li>
          </ul>
  </div>
  ```

  

+ `JS`实现原理

  ```javascript
   		// 获取 UL
  		var _uL = document.querySelector('.uL');
  		// 获取 UL下的 所有 li 标签
          var _lis = _uL.querySelectorAll('li');
          // 外层循环添加背景颜色
          for (var i = 0; i < _lis.length; i++) {
              // 清除原有 li 背景颜色
              _lis[i].onclick = function () {
                  for (var i = 0; i < _lis.length; i++) {
                      _lis[i].style.background = '';
                  }
                  // 添加新的背景色
                  this.style.background = 'red';
              }
          }
  ```

  

###   百度换肤效果

+ 方案一(拥有默认皮肤)

  ```less
   .box ul {
              list-style: none;
              width: 700px;
              margin: 100px auto;
          }
  
          .box ul li {
              float: left;
              margin-right: 10px;
          }
  
          .box ul li img {
              width: 200px;
              height: 200px;
              border: 5px solid red;
          }
  
          body {
              // 默认皮肤
              background: url(img/changeBg01.jpg) no-repeat;
              background-size: cover;
          }
  ```

+ `JS`获取点击事件并切换图片

  ```javascript
  / 获取 ul 和 图片
          var _imgs = document.querySelector('.ul').querySelectorAll('img');;
          // 循环遍历点击事件
          for (var i = 0; i < _imgs.length; i++) {
              _imgs[i].onclick = function () {
                  // console.log(this); this 指向 img 标签
                  var body = document.body.style.backgroundImage = 'url(' + this.src + ')';
              }
          }
  ```

+ 方案二(不存在皮肤)

+ `css`区别

  ```less
  body{
      background-size: cover;
  }
  ```

+ `JS`区别

  ```javascript
   var body = document.body;
   body.background = this.src;
  ```

+ `html`结构

  ```html
    <div class="box">
          <ul class="ul">
              <li> <img src="img/changeBg01.jpg" alt=""></li>
              <li> <img src="img/changeBg02.jpg" alt=""></li>
              <li> <img src="img/changeBg03.jpg" alt=""></li>
          </ul>
      </div>
  ```

  

+ 换肤效果演示

  <img src="https://img-blog.csdnimg.cn/20201128000814229.gif" width="600" alt="百度换肤" title="百度换肤">

###  表格鼠标移入添加底色

+ <font color="green">疑问(为什么可以直接从 `tbody` 获取)</font>

+ 实现效果演示

  <img src="https://img-blog.csdnimg.cn/20201128004400195.gif" alt="跟随换色" title="跟随换色">

+ 实现原理

  + 添加一个类(用来存放鼠标滑入时修改的样式)
  + 鼠标划入添加该类
  + 鼠标移出设置为空

+ `css`实现源码

  ```less
   table {
              width: 600px;
              text-align: center;
              line-height: 35px;
              margin: 100px auto;
              border-collapse: collapse; // 合并表格边框
          }
  
          caption {
              border: 1px solid #000;
              border-bottom: 0;
          }
  		// 后期使用修改样式的类
          .changeBg {
              background-color: #0099ff;
              color: #fff;
              transition: all .5s ease-in-out;
          }
  ```

+ `html`结构

  ```html
  <table border="1">
          <caption>百度换肤效果</caption>
          <thead>
              <tr>
                  <th>内容一</th>
                  <th>内容一</th>
                  <th>内容一</th>
                  <th>内容一</th>
                  <th>内容一</th>
              </tr>
          </thead>
          <tbody>
              <tr>
                  <td> 1 </td>
                  <td> 2 </td>
                  <td> 3 </td>
                  <td> 4 </td>
                  <td> 5 </td>
              </tr>
              <tr>
                  <td> 1 </td>
                  <td> 2 </td>
                  <td> 3 </td>
                  <td> 4 </td>
                  <td> 5 </td>
              </tr>
              <tr>
                  <td> 1 </td>
                  <td> 2 </td>
                  <td> 3 </td>
                  <td> 4 </td>
                  <td> 5 </td>
              </tr>
              <tr>
                  <td> 1 </td>
                  <td> 2 </td>
                  <td> 3 </td>
                  <td> 4 </td>
                  <td> 5 </td>
              </tr>
          </tbody>
      </table>
  ```

+ `JS`实现原理

  ```javascript
    // 获取元素 获取的是 tbody 里面所有的行
          var trs = document.querySelector('tbody').querySelectorAll('tr');
          for (var i = 0; i < trs.length; i++) {
              trs[i].onmouseover = function () {
                  this.className = 'changeBg';
              }
              trs[i].onmouseout = function () {
                  this.className = '';
              }
          }
  ```

  

###  全选按钮

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201128122431958.gif" alt="全选按钮案例" title="全选按钮案例">

+ `CSS`

  ```less
    table {
              width: 300px;
              line-height: 35px;
              margin-top: 100px;
              text-align: center;
              border-collapse: collapse;
              background-color: rgb(238, 241, 238);
              color: rgb(149, 168, 192);
          }
  
          caption {
              border: 1px solid #000;
              border-bottom: 0;
              background-color: #0099ff;
              color: #fff;
              font-weight: bold;
          }
  
          thead tr {
              background-color: #0099ff;
              color: #fff;
          }
  ```

+ `html`结构

  ```html
  <table border="1" align="center">
          <caption> 今日份水果菜单 </caption>
          <thead>
              <tr>
                  <th> <input type="checkbox" class="all"></th>
                  <th> 商品分类 </th>
                  <th> 价钱 </th>
              </tr>
          </thead>
          <tbody>
              <tr>
                  <td><input type="checkbox"> </td>
                  <td> 桃子</td>
                  <td> $3.99</td>
              </tr>
              <tr>
                  <td><input type="checkbox"> </td>
                  <td> 苹果</td>
                  <td> $10.99</td>
              </tr>
              <tr>
                  <td><input type="checkbox"> </td>
                  <td> 迷糊桃</td>
                  <td> $9.99</td>
              </tr>
          </tbody>
      </table>
  ```

+ `JS`实现原理

  ```javascript
    // 获取第一个checkbox
          var all = document.querySelector('.all');
          // 获取tbody 中 tr 下的 checkbox
          var _checkboxs = document.querySelector('tbody').querySelectorAll('input');
          all.onclick = function () {
              // 点击全选后的操作
              for (var i = 0; i < _checkboxs.length; i++) {
                  _checkboxs[i].checked = this.checked;
              }
          }
          // 复选框影响全选按钮
  
          for (var i = 0; i < _checkboxs.length; i++) {
              // 外层循环绑定每个复选框的点击事件
              _checkboxs[i].onclick = function () {
                  var flag = true;
                  for (var i = 0; i < _checkboxs.length; i++) {
                      // 首次进入状态为不选中,当点击后将会触发一个状态 true,如果有一个 _checkboxs为选中,那么flag = false
                      if (!_checkboxs[i].checked) {
                          flag = false;
                          break;
                      }
                  }
                  // 在检查完所有的 _checkboxs 都选中时,此时全选按钮的状态改为 true
                  all.checked = flag;
              }
          };
  ```

### `element.getAttribute()`

+ 获取属性值
  + `element.属性` 获取属性值
  + `element.getAttribute('属性')`

+ 区别

  + `element.属性` 获取内置属性值(元素本身自带的属性)

  + `elemetn.getAttribute('属性')`主要获得自定义的属性

+ 设置属性值

  + `element.属性='值'`
  + `element.setAttribute('属性','值')`

+ 特殊设置类

  > `元素.setAttribute('class','新值')`   // `class` 特殊 写的时 `class `不是 `className`

  

###  应用`element.getAttribute()和element.setAttribute()`

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201128122848312.gif" alt="选项卡功能" title="选项卡功能">  

+ `css`实现

  ```less
   * {
              margin: 0;
              padding: 0%;
          }
  
          .box ul {
              width: 1200px;
              list-style: none;
              margin: 50px auto;
          }
  
  
  
          .box ul li {
              width: 200px;
              height: 35px;
              text-align: center;
              line-height: 35px;
              padding: 10px;
              float: left;
              color: #ffffff;
              background-color: purple;
              border: 1px solid #ccc;
              cursor: pointer;
              transition: all .5s;
          }
  
          .box ul li.changeBg {
              background-color: red;
          }
  
          .box {
              position: relative;
          }
  
          .conetnet {
              position: absolute;
              left: 170px;
              top: 107px;
              clear: both;
              font-size: 30px;
              color: blue;
          }
  
          .conetnet .item {
              width: 1000px;
              height: 100px;
              display: none;
              border: 10px solid red;
          }
  ```

+ `html`结构

  ```html
  <div class="box">
          <ul class="tab-ul">
              <li>我是Tab-1</li>
              <li>我是Tab-2</li>
              <li>我是Tab-3</li>
              <li>我是Tab-4</li>
              <li>我是Tab-5</li>
          </ul>
      </div>
      <div class="conetnet">
          <div class="item" style="display: block;"> Tab-1</div>
          <div class="item"> Tab-2</div>
          <div class="item"> Tab-3</div>
          <div class="item"> Tab-4</div>
          <div class="item"> Tab-5</div>
      </div>
  ```

+ `JS`实现原理

  ```javascript
  // 获取元素 
          /*
          参与元素：
              ul li content item 属性 display
          */
           // 获取 ul
          var _tabul = document.querySelector('.tab-ul');
          // 获取 ul 下的所有 li
          var _lis = _tabul.querySelectorAll('li');
          // 获取所有的 item
          var content = document.querySelector('.conetnet');
          var items = content.querySelectorAll('.item');
  
          // 获取所有 li 的点击事件
          for (var i = 0; i < _lis.length; i++) {
              // 给所有的 li 设置一个属性 index
              _lis[i].setAttribute('index', i);
              _lis[i].onclick = function () {
                  console.log('点击中');
                  // 排除其他按钮的背景颜色
                  for (var i = 0; i < _lis.length; i++) {
                      _lis[i].className = '';
                  }
                  this.className = 'changeBg';
                  // 获取自定义属性值
                  var index = this.getAttribute('index');
                  console.log(index);
                  // item 排它思想
                  for (var i = 0; i < items.length; i++) {
                      items[i].style.display = 'none';
                  }
                  // 点击之后显示内容 先获取点击了那个 li ,再让对应的 item 显示为 display = block
                  items[index].style.display = 'block';
              }
          }
  ```


###  命名规范

> `date-`



###  节点操作

```javascript
父节点获取: 变量名.parentNode

子节点获取: 名.childNodes(包含所有节点 换行,空格 不建议)

		   名.children
```

+ `html`结构

  ```html
   <ul class="ul">
          <li>内容1</li>
          <li>内容2</li>
          <li>内容3</li>
          <li>内容4</li>
          <li>内容5</li>
      </ul>
  ```

+ `JS`原理分析

  ```javascript
      var _ul = document.querySelector('.ul');
      var _children = _ul.children;
      console.log(_children);
  ```

+ `children`使用演示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/children.png" alt="children使用演示" title="children使用演示">

```javascript
	// 获取内容一节点

​    var first = _ul.children[0];

​    console.log(first);

​    // 获取最后一个节点

​    var last = _ul.children[_ul.children.length - 1];

​    console.log(last);
```



###  导航栏案例实现

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201128175057611.gif" alt="Nav 二级显示隐藏" title="Nav 二级显示隐藏">

+ `css`源码

  ```less
  * {
              margin: 0;
              padding: 0;
          }
  
          body {
              background-color: #ccc;
          }
  
          .box {
              width: 600px;
              height: 100%;
              margin: 100px auto;
          }
  
          .box>ul {
              width: 100%;
              text-align: center;
              list-style: none;
          }
  
          .box>ul>li {
              position: relative;
              float: left;
              padding: 10px;
              border: 1px solid #ccc;
              width: 85px;
              background-color: skyblue;
          }
  
          .box>ul>li:hover {
              background-color: rgba(0, 0, 0, .5);
              transition: all .5s ease-in-out;
          }
  
          a {
              color: #fff;
              text-decoration: none;
          }
  
          .box>ul>li ul {
              position: absolute;
              display: none;
              left: 0;
              top: 41px;
              width: 105px;
              text-align: center;
  
              list-style: none;
          }
  
          .box>ul>li ul li {
              box-sizing: border-box;
              height: 45px;
              line-height: 45px;
              background: rgba(0, 0, 0, .5);
              border: 1px solid #ccc;
          }
  
          .box>ul>li ul li:hover {
              background-color: skyblue;
              transition: all .5s;
          }
  ```

+ `html`结构

  > <font color="purple" size=4>**结构Ement 语法: .box>ul>(li>a[href=#]+ul>li>a[href=#])*4** </font>

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
              <li>
                  <a href="#"> 充值中心 </a>
                  <ul>
                      <li> <a href="#"> 话费充值 </a></li>
                      <li> <a href="#"> 游戏充值 </a></li>
                      <li> <a href="#"> APStore充值 </a></li>
                  </ul>
              </li>
  
              <li>
                  <a href="#"> 消费者权益</a>
                  <ul>
                      <li><a href="#"> 消费者告知书</a></li>
                  </ul>
              </li>
              <li>
                  <a href="#"> 更多 </a>
                  <ul>
                      <li> <a href="#"> 收藏本站 </a></li>
                      <li> <a href="#"> 新浪微博 </a></li>
                      <li> <a href="#"> 微信公众号 </a></li>
                      <li> <a href="#"> 招商合作 </a></li>
                  </ul>
              </li>
          </ul>
      </div>
  ```

+ `JS`原理分析

  ```javascript
  		// 获取 第一个 ul
          var _parentUl = document.querySelector('.ul');
          // 获取第一个 ul 下的 li(伪数组)
          var lis = _parentUl.children;
          // 遍历添加鼠标移入移出事件
          for (var i = 0; i < lis.length; i++) {
              lis[i].onmouseover = function () {
                  // 获取第二个ul 并修改display = block
                  //console.log(this); 1 == ul.display = 'block';
                  this.children[1].style.display = 'block';
              }
              lis[i].onmouseout = function () {
                  // 获取第二个 ul 并修改display = block
                  // console.log(this);
                  this.children[1].style.display = 'none';
              }
          }
  ```

  

###  创建节点

+ 效果演示

<img src="https://img-blog.csdnimg.cn/20201128190959503.gif" alt="子节点添加-留言" title="子节点添加-留言" width="450">

+ `css`实现源码

  ```less
  * {
              margin: 0;
              padding: 0;
          }
  
          body {
              background-color: rgb(66, 22, 22);
          }
  
          .box {
              width: 600px;
              height: 100%;
              margin: 100px auto;
          }
  
          .box button {
              display: inline-block;
              width: 100px;
              height: 35px;
              margin-left: 20px;
              line-height: 31px;
          }
  
          label {
              text-align: center;
              display: block;
              border: 1px solid #09f;
              height: 100px;
              line-height: 100px;
          }
  
          .box input {
              color: #999;
              box-sizing: border-box;
              display: inline-block;
              height: 35px;
              padding: 5px;
              line-height: 40px;
              border: none;
              transition: all .5s;
          }
  
          .message {
              border: 2px solid blue;
              width: 597px;
              height: 400px;
              line-height: 35px;
              overflow: auto;
          }
  
          li {
              color: #fff;
              margin-left: 30px;
          }
  ```

+ `html`结构

  ```html
  <div class="box">
          <label for="message">
              <input type="text" value="请输入留言信息" /><button value="回复留言"> 留言</button>
          </label>
  
          <ul class="message">
              <li>asa</li>
          </ul>
  
      </div>
  ```

+ `JS`原理分析

  ```javascript
  // input 获取焦点时 value 文字消失
          var text = document.querySelector('input');
          text.onfocus = function () {
              // console.log('input 获取焦点···');
              if (this.value === '请输入留言信息') {
                  this.value = '';
                  // console.log('走到这里了···');
              }
              this.style.border = '2px solid #09f';
              // 修改 value 文字样式 #ccc
              this.style.color = '#ccc';
          }
          // 文字失去焦点时 value 文字显示
          text.onblur = function () {
              if (this.value === '') {
                  this.value = '请输入留言信息';
              }
              this.style.color = '#999';
          }
          // 获取 button
          var btn = document.querySelector('button');
          // 获取 ul
          var ul = document.querySelector('.message');
          // console.log(btn.value);
          btn.addEventListener('click', function () {
              // console.log('点击了按钮');
              // 点击按钮创建子节点 li
              var lis = document.createElement('li');
              // 并添加在 ul 中
              lis.innerHTML = text.value;
             	// 最后面显示
              ul.appendChild(lis); 
              
            // 最前面显示
             // ul.insertBefore(lis,ul.children[0]);
          });
  ```
  
  

###  删除节点

> `node.removeChild(child)` 该方法从`DOM`中删除一个子节点,返回删除的节点

+ 疑惑: `addEventListener`监听的点击事件 `alert`依然会触发

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201128235935743.gif" alt="removeChild()" title="removeChild()">

+ `css`源码

  ```less
  ···
  ```

+ `html`结构

  ```html
   <ul>
          <li> 内容一</li>
          <li> 内容二</li>
          <li> 内容三</li>
      </ul>
      <button> 删除节点 </button>
  ```

+ `JS`

  ```javascript
  var _ul = document.querySelector('ul');
  var lis = _ul.children;
  var btn = document.querySelector('button');
   btn.onclick = function () {
              if (_ul.children.length == 0) {
                  alert('内容已经清空···');
                  this.disabled = true;
              } else {
                  _ul.removeChild(_ul.children[0]);
              }
          };
  ```

###   复制节点

```javascript
 		var _ul = document.querySelector('ul');
        // 克隆了第一个元素  如果括号参数为 空或者为 false 则是浅拷贝,即克隆复制节点本身,不克隆里面的子节点
        var cloneL = _ul.children[0].cloneNode(true);
        // 括号为 true 深拷贝 复制标签里面的内容
        _ul.appendChild(cloneL)
```

###  `DOM`-`增删改查`总结

+ 创建
  + `document.write`
  + `innerHTML`
  + `createElement`

+ 删除
  + `removeChild()`
+ 插入
  + `appendChild`
  + `insertBefore`
+ 修改
  + 属性修改`href,scr,title`
  + 普通元素内容修改
  + 表单元素修改`value,type,disabke`
  + 修改元素样式`style,className`



###   事件对象阻止默认行为

```javascript
function fn(e){
    e.preventDefault(); // dom 标准
    
    或者
    
    return false; // 传统方式 后面内容不执行
}
```



###  阻止事件冒泡

```javascript
e.stopPropagation()

e.cancelBubble = true; // 非标准 canel 取消 冒泡
```

###  事件委托

+ 事件委托

  ```javascript
  事件委托也称为事件代理,在 jQuery 里面称为事件委派
  ```

+ 事件委托原理

  ```javascript
  不是每个子节点单独设置事件监听器,而是事件监听器设置在其父节点上,然后利用冒泡原理影响设置每个子结点
  ```

+ 案例

  ```javascript
  // 发现点击了 ul 区域会全变色，单一点击也会单一变色
          var ul = document.querySelector('ul');
          var lis = ul.children;
          ul.addEventListener('click', function (e) {
              for (var i = 0; i < lis.length; i++) {
                  lis[i].style.backgroundColor = '';
              }
              e.target.style.backgroundColor = 'red';
          });
  
  -----------------------------------------------------------------------------
   //   点谁谁变色     
          for (var i = 0; i < lis.length; i++) {
              lis[i].onclick = function () {
                  for (var i = 0; i < lis.length; i++) {
                      lis[i].style.background = '';
                      lis[i].style.color = '';
                  }
                  this.style.color = '#fff';
                  this.style.background = 'purple';
              }
          }
  
  ```

  

