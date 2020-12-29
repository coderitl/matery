---
title: Hexo-统一定位符(url)-引起错误解决方案
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: Hexo
categories: Hexo
abbrlink: 1764
date: 2020-11-29 23:07:04
top_img:
cover:
---



###  Hexo-统一定位符(url)-引起错误解决方案

+ 在起初由于文章过多(`全部显示在 _posts下`) 
  + 配置 `permalink`
  + 配置 `new_post_name`

+ 在提交文章内容后本地可预览状态 - `gitpages`路径中出现小写

  > `Eg.`
  >
  > `lovobin.github.io/2020/hexo/Hexo-统一定位符-url-引起错误解决方案/` （**正确显示**）
  >
  >  `lovobin.github.io/2020/Hexo/Hexo-统一定位符-url-引起错误解决方案/`(**错误显示**)
  >
  > `hexo`  不等于 `Hexo`（导致无法显示）

+ 引起上述错误解决方案

  + 在博客根目录下找到如下文件夹

    `.deploy_git` 需要开启

    <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/hiddenBlog.png">

  + 进入`.deploy_git`

  + 再进入`.git`

  + 使用编辑器打开`config`配置文件

  + 修改如下参数

    ```bash
    ignorecase = true 改为 ignorecase = false
    ```

  + 再不信任的情况下剪切出  除`.git`文件之外的文件到其他路径下暂存

  + 进行如下操作

    ```bash
    git rm -rf * (等价于剪切 因为剪切后文件不存在)
    git commit -m ‘clean all file’  (提交日志信息)
    git push  (推送)
    ```

+ 返回博客根目录重新部署

  ```bash
  hexo clean
  hexo g
  hexo -d
  ```

+ 进入博客网站

  > 强制刷新:  `ctrl+F5`



