---
title: Javascript-常用鼠标事件
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 3600
date: 2020-11-29 11:56:16
top_img:
cover:
---

###  常用鼠标事件

+ 禁用鼠标右键菜单

  ```javascript
   document.addEventListener('contextmenu', function (e) {
              e.preventDefault();
          });
  ```

+ 禁止文本选中

  ```javascript
   document.addEventListener('selectstart', function (e) {
              e.preventDefault();
          });
  ```

  