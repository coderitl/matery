---
title: JavaScript-offset系列
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 41656
date: 2020-12-01 16:38:58
top_img:
cover:
---

### offset 概述

> `offset` 就是偏移量 使用 `offset 系列相关的属性`可以动态的得到该元素得位置(偏移) 

+ 获得元素距离带有定位父元素的位置

+ 获得元素自身的大小(宽度高度)

+ 返回的数值不带单位



+ `offset`系列常用属性

  |    `offset`系列属性    |                            作用                             |
  | :--------------------: | :---------------------------------------------------------: |
  | `element.offsetParent` | 返回该元素带有定位的父级元素,如果父级都没有定位则返回`body` |
  |  `element.offsetTop`   |            返回元素相对带有定位父元素上方的偏移             |
  |  `element.offsetLeft`  |            返回元素相对带有定位元素左边框的偏移             |
  | `element.offsetWidth`  |  返回自身包括padding、边框、内容区的宽度、返回数值不带单位  |
  | `element.offsetHeight` | 返回自身包括 padding、边框、内容区域的高度,返回数值不带单位 |

  