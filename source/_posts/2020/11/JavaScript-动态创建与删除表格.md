---
title: JavaScript-动态创建与删除表格
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 46645
date: 2020-11-29 09:59:09
top_img:
cover:
---

###  动态创建表格

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201129100114223.gif" alt="JavaScript-动态创建表格" title="JavaScript-动态创建表格" width="600">

  

+ `css`源码

  ```less
  table {
              width: 600px;
              line-height: 40px;
              text-align: center;
              border-collapse: collapse;
              margin: 100px auto;
          }
  
          caption {
              border: 1px solid #000;
              border-bottom: 0;
              color: #fff;
              font-weight: bold;
              background-color: rgb(120, 173, 209);
          }
  
          th {
              background-color: rgb(120, 173, 209);
          }
  ```

+ `html`结构

  ```html
   <table align="center" border="1">
          <caption>动态创建表格</caption>
          <thead>
              <tr>
                  <th>姓名</th>
                  <th>科目</th>
                  <th>成绩</th>
                  <th>操作</th>
              </tr>
          </thead>
          <tbody>
  
          </tbody>
      </table>
  ```

+ `JS`原理分析

  ```javascript
  <script>
  
          // 模拟数据库
          var datas = [
              {
                  name: '张三',
                  subject: 'JavaScript',
                  grades: 90
              },
              {
                  name: '李四',
                  subject: 'Java',
                  grades: 80
              },
              {
                  name: '王麻子',
                  subject: 'Python',
                  grades: 90
              },
              {
                  name: 'Tom',
                  subject: 'JavaScript',
                  grades: 100
              }
          ];
          // 动态创建 tr td 根据对象创建
          for (var i = 0; i < datas.length; i++) {
              // 1. 先获取父级元素 
              var tbody = document.querySelector('tbody');
              // 创建 tr
              var tr = document.createElement('tr');
              // 将 tr 添加在 tbody 中
              tbody.appendChild(tr);
              // 准备创建列 需要遍历对象
              for (var k in datas[i]) {
                  // console.log(k); k == 对象的键
                  // 需要获取 k 的值
                  // console.log(datas[i][k]); 拿到 k 的值
                  // 创建 td 根据 k
                  var td = document.createElement('td');
                  // 在创建完 td 后需要拿到 k 的值
                  td.innerHTML = datas[i][k];
                  tr.appendChild(td);
              }
              // 创建删除单元格
              var td = document.createElement('td');
              td.innerHTML = '<a href="javascript:;">删除</a>';
              tr.appendChild(td);
          }
          // 删除操作 需要在创建完整表格再有删除
          // 获取所有的 a
          var allDelete = tbody.querySelectorAll('a');
          // 循环遍历
          for (var i = 0; i < allDelete.length; i++) {
              allDelete[i].onclick = function () {
                  // 删除 整行 node.removeChild(child) node=== 父节点
                  tbody.removeChild(this.parentNode.parentNode);
              }
          }
      </script>
  ```

  

