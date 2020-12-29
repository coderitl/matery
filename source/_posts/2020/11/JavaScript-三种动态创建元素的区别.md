---
title: JavaScript-三种动态创建元素的区别
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 11881
date: 2020-11-29 10:19:57
top_img:
cover:
---

###  三种动态创建元素的区别

+ `document.write()`
+ `element.innerHTML`
+ `document.createElement()`

####  区别

1. `docuemnt.write`是直接将内容写入特定的内容流,<font color="red">**但是文档流执行完毕,则它会导致页面全部重绘**</font>

2. `innerHTML` 是将内容写入某个`DOM`节点,不会导致页面全部重绘
3.  `innerHTML`创建多个元素效率更高(不要拼接字符串,采取数组形式拼接)
4. `createElement()`创建多个元素效率稍微低一点,但是接轨更加清晰

> **采取数组时,`innerHTML`效率要比`creatElement`高**