---
title: JavaScript-Location对象的属性
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 23058
date: 2020-12-01 15:11:29
top_img:
cover:
---



###  Location 对象的属性

|  Location 对象属性  |                返回值                |
| :-----------------: | :----------------------------------: |
|   `location.href`   |         获取或者设置整个 URL         |
|   `location.host`   |            返回主机(域名)            |
|   `location.port`   |   返回端口号,如果未写返回 空字符串   |
| `location.pathname` |               返回路径               |
|  `location.search`  |               返回参数               |
|   `location.hash`   | 返回片段 #后面的内容 常见于链接 锚点 |

###  Location 对象方法

| Location 对象方法  |                            返回值                            |
| :----------------: | :----------------------------------------------------------: |
| `location.assign`  |       跟 `href `一样,可以跳转页面（也成为重定向页面）        |
| `location.replace` |         替换当前页面,因为不记录历史,所以不能后退页面         |
| `location.reload`  | 重新加载页面,相当于刷新按钮或者 `F5 `如果参数为` true `强制刷新 `ctrl+F5` |



###  Location 应用

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201201154431714.gif" alt="location.href" title="location.href">

+ `css`

  ```less
   span {
              color: red;
              font-size: 20px;
              display: inline-block;
              width: 40px;
              height: 40px;
              line-height: 40px;
              text-align: center;
              background-color: #09f;
          }
  ```

+ `html`

  ```html
      <div>
          自动跳转
      </div>
  ```

+ `JS`

  ```javascript
  // 获取元素
          var div = document.querySelector('div');
          // 计时器
          var time = 5;
          // 调用该函数解决空白刷新
          showText();
  
          function showText() {
              if (time == 0) {
                  location.href = 'https://lovobin.github.io/'
              } else {
                  div.innerHTML = '您将在' + '<span>' + time + '</span>' + '秒后返回奔跑的小前端';
                  time--;
              }
          }
          // 开启定时器
          setInterval(function () {
              showText();
          }, 1000);
  ```

  

###  location.search

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201201160351281.gif" alt="location.search" title="location.search">

+ `login.html`

  + `css`

    ```less
    
    ```

  + `html`结构

    ```html
    <form action="index.html">
            <label for="text">
                <input type="text" id="text" name="uname">
                <input type="submit" value="登录">
            </label>
        </form>
    ```

+ `index.html`

  + `css`

    ```less
    
    ```

  + `html`结构

    ```html
    <div></div>
    ```

  + `JS`原理分析

    ```javascript
     		var div = document.querySelector('div');
            console.log(location.search); // ?uname=input.value
            // 字符串截取
            var str = location.search;
            var newStr = str.substr(1);
            console.log(newStr); // uname=input.value
            // 分割字符串 
            var arr = newStr.split('=');
            console.log(arr);
            var parmer = arr[1];
            div.innerHTML = parmer;
    ```

    



