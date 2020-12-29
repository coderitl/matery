---
title: Hexo-樱花特效添加
tags:
  - Hexo
  - matery
  - JS特效
  - 教程
categories: matery-theme
abbrlink: 46045
date: 2020-12-29 17:27:30
---

###  樱花飘落特效

+ 效果演示

  <img src="https://img-blog.csdnimg.cn/20201229175522499.gif" titke="樱花飘落" alt="资源加载中···" width="800" height="200">

+ 具体实现步骤

  ```bash
  1. 进入 themes\hexo-theme-matery\source\libs\others 文件夹下
  ```

  ```bash
  2. 新建文件 sakura.js
  ```

  ```bash
  3. 点击进入: 
  	# 樱花效果 如遇其他效果同理步骤
  	https://cdn.jsdelivr.net/gh/Yafine/cdn@2.5/source/js/sakura.js
  ```

  ```bash
  4. 复制上述链接内容至 sakura.js
  ```

  ```bash
  5. 进入 themes\hexo-theme-matery 下的配置文件: _config.yml
  ```

  ```bash
  6. 搜索 libs (引入样式的地方)
  ```

  ```bash
  7. 在 js 下的最后一行添加: sakura: /libs/others/sakura.js
  ```

  ```bash
  8. themes\hexo-theme-matery\layout\layout.ejs里添加如下代码:
  	
  	+ 具体位置(测试了几处位置都失败,请尽量参考如下):
  	+ 进入第八步骤打开文件在第 8 ~ 9 空白处添加如下代码片段
  	
  	<% if (theme.sakura.enable) { %>
  		<script type="text/javascript" src="<%- theme.libs.js.sakura %>"></script>
  	<% } %>
  ```

  ```bash
  9. 主题配置文件中(hexo-theme-matery\_config.yml)添加:
      # 樱花
      sakura: 
          enable: true
  ```

  

###  文章显示短链接

+ 下载插件

  ```bash
  npm install hexo-abbrlink --save  
  ```

+ 在` Hexo `根目录下的 `_config.yml `文件中，修改 `permalink:` ，并在文件末尾新增 `abbrlink:`配置项：

  ```bash
  # 显示状态配置
  permalink: :year/:month:day:abbrlink.html
  ```

  ```bash
  # hexo 根目录下配置文件中添加如下信息 (加载由上而下)注意位置
  abbrlink: 
    alg: crc16 #算法选项：crc16丨crc32
    rep: dec #输出进制：dec为十进制，hex为十六进制
  ```

###  Hexo 端口号问题

+ 修改被占用端口号

  ```bash
  错误状态:
  	 code: 'EADDRINUSE',
       errno: -4091,
       syscall: 'listen',
       address: '::',
       port: 4000
  ```

+ 进行如下操作

  ```bash
  hexo s -p端口号数值(任意)
  # 例如使用 5000 端口号
  Eg. 
  	hexo s -p5000
  ```

  



