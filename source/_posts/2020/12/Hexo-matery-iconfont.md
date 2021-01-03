---
title: Hexo matery-iconfont
abbrlink: 22036
date: 2020-12-31 12:14:29
tags: 
- Hexo
- matery
- iconfont
categories: matery-theme
---

###  Hexo matery-iconfont:

> <a href="https://www.iconfont.cn/">跳转ICON-FONT: https://www.iconfont.cn/</a>

+ 登录 `or` 注册 阿里矢量图库

+ 挑选想用图标

+ 添加至购物车

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231122502.png">

+ 添加至项目

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231122616.png" height="300">

+ 进入项目

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/iconfontcss.png">

+ 选中`点击复制代码下的链接`

  > 进入该链接,获取图标的`css`样式

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231122822.png">

+ （已经生效，使用该方法）选中所有信息复制到`matery: my.css中`

  > 使用该方法的理由:  
  >
  >  1. 由于使用外链引入,不知为何不生效(已经考虑了权重问题)
  >
  >  2.  下载了`font`的压缩包引入未生效
  >
  >     

+ 修改

  + 原样式

    <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231123400.png" width="600">

  + 修改后

  + 效果查看

    ```html
    修改内容:
    	+ 添加 link 图标
    	+ 添加 hover 效果
    	+ 修改显示颜色
    ```

    <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/h16.gif" title="h1~h6: Hover">

  + 修改`my.css`

    ```css
    /* my.css 全部内容 */
    /* Here is your custom css styles. */
    @font-face {
      font-family: "iconfont";
      src: url("//at.alicdn.com/t/font_2301842_zbxhtw82wpa.eot?t=1609385220731"); /* IE9 */
      src: url("//at.alicdn.com/t/font_2301842_zbxhtw82wpa.eot?t=1609385220731#iefix")
          format("embedded-opentype"),
        /* IE6-IE8 */
          url("data:application/x-font-woff2;charset=utf-8;base64,d09GMgABAAAAAANUAAsAAAAABzQAAAMFAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHEIGVgCCcAqCQIIXATYCJAMICwYABCAFhG0HLhs7BhHVk/9kf0nuVG0v4EQocLqiZycaymFh22Qvr1glm4PFLC6xH2LSM8EDv7/3XPz/7/ecyLZ1CFFKS3Ta4kIRKtSlhjqH/I62OfGSLiQskjbvmsB3r+hxs78fV7tOQmiukvLORpWyvvvvoLZsB0YwGfnsAWeXC5FlGbkAeIkyuJ0D8ZhiL2Pq//vNkvdXGUwEwMLhtCt+B5RagPdcPBcwsDTQc69gViCBecPYBS9wPQTgIlI6kW8vr8egsbsJQAwUu1sxBRsazYIGgb1hrEasMsfIZRlGrETfF78EGZDYFHZa9RZ0kP0kJ0xNWY2iAAF9OQ3AJoEC0oEGUd+oq6QSXzqFS/dpYnGsZAGfrAPaYf94IEDYsRM9AIRD2jPRPcajJkoAdNLYAcYnpYPMgJyrc0c2uyv93SyJXcUR10XAgR4vMj3NneOO+Tv2jSvlkTB6dRW7vk40HDJXurmKatEsZ10GPN63uttq64fSfW2IF3mHPjuIEGeWAyPO9vWt5lSSuL3hlcLH5drucPa0QrqOUONnCH2qXQ87tXEzbRrqavDbl79sS3PCO1MhcNxu+0OO69JIbcM7rj7I2tmDqPuVXO2/mp/ZnajvDgTF4WriFUHGqLwxztHzFLoJQCimntgCsG561fLnf0Pf/L8Kfm2GBuBtFyGyWDfDMAOY+9ML+M/0gRXaYNpyqTV6o0HSMamrBFy4AAs2BfmYKgp9qZDAEPpqBgcRGSgM8UiNTQcbbjLBjiELXKQpmuwm2CCF0E4g1TwAQYBDkPi4BEWAW6TGvoONMP9gJyAFLhpjzekmMURvDoQ54wuKP+iybYSr5E2cfEX5rnLKMyPcE2nQTvAdrxy8YIO0xIDhIwNmAYLaGs5gM6yqFjpqDZbsKOYudF3R9CKnbOvRZnQgzBlfUPxBl20jgvq8qXz+ivJd5dSRUyd/Ig26efAdbwDywmsG5TzKJcNHBswCBLU1nIEGK8fXQtfcymDJjprg6UIX1RJDec72gvoHUlkBtliOnWzFrNKNHY0AAAAA")
          format("woff2"),
        url("//at.alicdn.com/t/font_2301842_zbxhtw82wpa.woff?t=1609385220731")
          format("woff"),
        url("//at.alicdn.com/t/font_2301842_zbxhtw82wpa.ttf?t=1609385220731")
          format("truetype"),
        /* chrome, firefox, opera, Safari, Android, iOS 4.2+ */
          url("//at.alicdn.com/t/font_2301842_zbxhtw82wpa.svg?t=1609385220731#iconfont")
          format("svg"); /* iOS 4.1- */
    }
    
    .iconfont {
      font-family: "iconfont" !important;
      font-size: 16px;
      font-style: normal;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
    }
    
    .icon-link:before {
      content: "\e706";
    }
    #artDetail #articleContent #toc-heading-1::before,
    #artDetail #articleContent #toc-heading-2::before,
    #artDetail #articleContent #toc-heading-3::before,
    #artDetail #articleContent #toc-heading-4::before {
      display: inline-block;
      font-family: "iconfont" !important;
      content: "\e706";
      height: 0;
      margin-top: 0;
      visibility: visible;
      color: #f47466;
      padding-right: 5px;
    }
    html,
    body {
      font-size: 14px;
    }
    #artDetail #articleContent h1:hover,
    #artDetail #articleContent h2:hover,
    #artDetail #articleContent h3:hover,
    #artDetail #articleContent h4:hover {
      cursor: pointer;
      color: #f47466;
      padding-left: 10px;
      transition: all 0.5s ease-in;
    }
    
    ```

    