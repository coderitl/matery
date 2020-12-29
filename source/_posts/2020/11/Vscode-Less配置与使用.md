---
title: Vscode-Less配置与使用
tags: less
cover: 'https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/lessBg.png'
abbrlink: 51278
date: 2020-11-11 15:20:18
top_img:
---

###  `Vscode配置Less`：

+ 全局`node`安装

  > ```bash
  > npm install -g less
  > ```

+ 手动编译

  > ```js
  >  lessc styles.less styles.css
  > ```

+ 安装插件

  > ```bash
  > Easy Less
  > ```

+ `Less配置`

  ```bash
     // Less 配置
      "less.compile": {
          "compress": false,// 去除多余空格
          "sourceMap": true,// 生成 map 文件
          "out": "..\\css\\", // 这里是代表编译后生成的css文件所放的位置
      },
  ```

+ 添加在`settings.json`中

+ > `file(文件)-->Preferences(首选项)-->Settings`
  >
  > <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/lessS.png" width="400">
  >
  > <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/less-U.png" width="1000">

+ 效果展示

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/less-R.png" width="800">

+ 实时渲染效果

  <img src="https://img-blog.csdnimg.cn/20201111155059947.gif#pic_center">

+ `Mixins`

  ```less
  通过 Mixins 可以将不同类的样式进行混合使用
  
  1.类名{
     类选择器(); // 复用 
  }
  
  2. 类名:extend(类名 [all]){
      
  }
  
  // 定义 Mixins 时,如果在名字后面添加了()则 mixin 中的样式不会被编译到 css 文件中
  // 定义时,可以在() 中指定参数,这个参数就相当于定义了一个变量,但是并没有赋值
  
  类名(@变量名){
      width: @变量名; // 可以使用默认值 也可以传递参数
  }
  
  类名(@变量名: 默认值){
      width: @变量名; // 可以使用默认值 也可以传递参数
  }
  
  ```

+ 模块化编写`css`

  ```less
  @import "less文件";
  ```

  

+ Less中文文档推荐

  > `https://less.bootcss.com/`