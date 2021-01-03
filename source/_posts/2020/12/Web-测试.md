---
title: Web-测试
abbrlink: 43474
date: 2020-12-31 13:13:09
tags:
---

###  Web-测试
+ 什么是 web 测试？

  > Web 测试属于软件测试的范畴,是针对 Web 服务特征进行的软件测试工作。由于Web 应用于用户直接相关,通常需要长时间的大量操作,因此需要针对 Web 项目展开全面测试,保障 Web项目功能和性能的可靠性。

+ 测试内容
  + 功能测试
    - 主要针对具体功能测试，主要包括链接，表单测试，数据验证Cookies···
  + 性能测试
    - 针对高并发，高压力下服务情况测试
  + 用户界面测试
    - 主要针对 Web 和 UI测试···
  + 兼容想测试
  + 安全测试
  + 接口测试
+ 测试目的
  - 验证 Web 需求和功能是否得到完整实现，再正常情况和非正常情况下的功能显示状态
  - 发现Web的缺陷,错误,进而较为准确的推测出Web 应用潜在缺陷,获取Web 应用的质量信息
  - 根据当前发现的问题进行分析，为下一步开发提供支持
  - 发现影响用户使用的错误,预防用户访问或使用时可能出现的问题
  - 通过测试结果数据,测试问题记录等数据，了解并分析Web 应用存在的问题,提高Web开发效率
  - 验证Web 是否可以发布并使用

+ 平台兼容性测试

  > 使用 BrowserShots 在线测试工具
  >
  > 
  >
  > 官网地址:<a href=" http://browsershots.org">  http://browsershots.org</a </a>
  >
  > <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231133021.png">

+ 浏览器兼容性测试

  - 7种工具(知乎搜索)

  - 云工具

    ```html
    LambdaTest(https://www.lambdatest.com/)
    
    作为一款基于云的自动化跨浏览器测试平台，LambdaTest提供了2000多种浏览器和操作系统的组合，以方便您测试自己的Web应用程序。它可以让您在基于云的selenium grid上执行自动化的selenium脚本，并针对网页进行各种实时的交互式测试。LambdaTest能够提供自动化测试、实时测试、响应式测试、屏幕截图测试、以及可视化测试。如果您在测试Web应用或网站时遇到任何技术问题，LambdaTest都能提供24x7的全天候支持。可以说，它是最为常见的跨浏览器测试工具之一。
    
    ```

    <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231133810.png">

+ 分辨率测试

  - 测试结果

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231134331.png"  width="640">

  - 修改上图红框位置(`分辨率修改`)

  + `TestSize`官方网址

    > <a href="http://testsize.com">前往 http://testsize.com</a>

+ 功能测试
  - 链接测试
  - 软件···

+ 性能测试

  - 使用 Chrome的NetWork工具进行网页连接速度测试

  + `Timeline`

    - 蓝色线表示网络和`HTML` 解析时间

    - 紫色线表示 `DomContentLoaded `事件,即该时间点页面中的`DOM`建立完成,发生了 `DomContentLoaded`事件

    - 红色线表示 `load`事件,即该时间点页面加载完了所有资源,发生了`Load`事件将鼠标放到单个文件的时间轴上,会弹出时间加载每个阶段的详细信息

    <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231140124.png">

    + 绿色线表示网页渲染和绘制时间

      加载中每个阶段的过程及含义

      - `Stalled`请求处于阻塞状态
      - `Proxy negotiation` 与代理服务器的连接通信阶段
      - `DNS Lookup` DNS 查找阶段
      - `Initial Content/connecting` 建立连接的过程,包含 `TCP`握手/重试
      - `SSL`完成`SSL`握手阶段
      - `Request sent`发送请求
      - `Waiting(TTFB)`发出请求后等待服务器响应的时间,响应时间为第一个字节发送过来的时间
      - `Content Download` 接受响应数据的时间

  + 使用`Pingdom Tools`分析网站访问性能

    > 简介
    >
    > PringDom 是免费在线网站速度检测工具
    >
    > + 主界面
    >
    > <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/pinfdom.png">

  + 对主站博客进行性能分析

    <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231141347.png">

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231141557.png">

+ 压力测试

  