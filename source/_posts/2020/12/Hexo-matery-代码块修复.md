---
title: Hexo matery 代码块修复
date: 2020-12-28 11:29:23
tags:

---



###  代码块在 matery 主题下的基本展示:

```python
# python
a = 10;
```

```html
<!-- HTML -->
<div calss="wrap">
    我是 wrap 内容
</div>
```

```javascript
/* js */
const timer = null
```

```css
/* css */
.wrap{
    width: 10px;
    height: 10px;
}
```

```java
// java
class People{
    int age = 18;
}
```

```sql
-- mysql 无法高亮
-- 推荐: sql
select * from dept;
```

```bash
# bash
npm install 
```

###  配置步骤详解

####  Matery 引起的问题罗列：

+ `root`路径配置
+ 需要`CDN`服务
+ 代码块显示异常

###   问题解决方案:

####  1. Root路径问题

+ `gitee`部署,需要添加仓库名`root/myBlog/`
+ 虚拟主机部署,`root/`

####  2. CDN 可查阅`JsDeliver`自行理解如何部署

####  3. 代码块显示异常解决

+ 安装代码块插件

  ```bash
  npm i -S hexo-prism-plugin
  ```

+ 配置`Hexo`根目录的`_config.yml`

  ```bash
  highlight:
    enable: false # 关闭原有的高亮代码
  
  # 添加prism_plugin配置项
  prism_plugin:
    mode: 'preprocess'    # realtime/preprocess
    theme: 'tomorrow'
    line_number: true    # default false
    custom_css: 
  ```

+ 配置`Matery-theme`根目录的`_config.yml`

  ```bash
  code:
    lang: true # 代码块是否显示名称
    copy: true # 代码块是否可复制
    shrink: true # 代码块是否可以收缩
    break: false # 代码是否折行
  ```

+ 修改代码块`css`

  ```css
  <!-- 打开themes\source\css\matery.css，大概在 100 到 200  行左右,修改代码块CSS样式如下 -->
  pre {
      padding: 1.5rem 1.5rem 1.5rem 3.3rem !important;
      margin: 1rem 0 !important;
      background: #272822;
      overflow: auto;
      border-radius: 0.35rem;
      tab-size: 4;
  }
  .code-area::after {
      content: " ";
      position: absolute;
      border-radius: 50%;
      background: #ff5f56;
      width: 12px;
      height: 12px;
      top: 0;
      left: 12px;
      margin-top: 12px;
      -webkit-box-shadow: 20px 0 #ffbd2e, 40px 0 #27c93f;
      box-shadow: 20px 0 #ffbd2e, 40px 0 #27c93f;
  }
  code {
      padding: 1px 5px;
      top: 13px !important;
      font-family: Inconsolata, Monaco, Consolas, 'Courier New', Courier, monospace;
      font-size: 0.91rem;
      color: #e96900;
      background-color: #f8f8f8;
      border-radius: 2px;
  }
  .code_copy {
      position: absolute;
      top: 0.7rem;
      right: 25px;
      z-index: 1;
      filter: invert(50%);
      cursor: pointer;
  }
  .codecopy_notice {
      position: absolute;
      top: 0.7rem;
      right: 6px;
      z-index: 1;
      filter: invert(50%);
      opacity: 0;
  }
  .code_lang {
      position: absolute;
      top: 1.2rem;
      right: 46px;
      line-height: 0;
      font-weight: bold;
      font-family: normal;
      z-index: 1;
      filter: invert(50%);
      cursor: pointer;
  }
  
  .code-expand {
      position: absolute;
      top: 4px;
      right: 0px;
      filter: invert(50%);
      padding: 7px;
      z-index: 999 !important;
      cursor: pointer;
      transition: all .3s;
      transform: rotate(0deg);
  }
  
  .code-closed .code-expand {
      transform: rotate(-180deg) !important;
      transition: all .3s;
  }
  
  .code-closed pre::before {
      height: 0px;
  }
  
  pre code {
      padding: 0;
      color: #e8eaf6;
      background-color: #272822;
  }
  
  pre[class*="language-"] {
      padding: 1.2em;
      margin: .5em 0;
  }
  
  code[class*="language-"],
  pre[class*="language-"] {
      color: #e8eaf6;
      white-space: pre-wrap !important;
  }
  
  .line-numbers-rows {
      border-right-width: 0px !important;
  }
  
  .line-numbers {
      padding: 1.5rem 1.5rem 1.5rem 3.2rem !important;
      margin: 1rem 0 !important;
      background: #272822;
      overflow: auto;
      border-radius: 0.35rem;
      tab-size: 4;
  }
  ```

+ 文章代码块添加

  ```javascript
  <!-- 存在则修改，简称添加 添加 cdn 后注意路径添加 -->
  <!-- 代码块功能依赖 -->
  <script type="text/javascript" src="<%- url_for('/libs/codeBlock/codeBlockFuction.js') %>"></script>
  
  <!-- 代码语言 -->
  <% if (theme.code.lang) { %>
  <script type="text/javascript" src="<%- url_for('/libs/codeBlock/codeLang.js') %>"></script>
  <% } %>
  
  <!-- 代码块复制 -->
  <% if (theme.code.copy) { %>
  <script type="text/javascript" src="<%- url_for('/libs/codeBlock/codeCopy.js') %>"></script>
  <% } %>
  
  <!-- 代码块收缩 -->
  <% if (theme.code.shrink) { %>
  <script type="text/javascript" src="<%- url_for('/libs/codeBlock/codeShrink.js') %>"></script>
  <% } %>
  
  <!-- 代码块折行 -->
  <% if (!theme.code.break) { %>
  <style type="text/css">
  code[class*="language-"], pre[class*="language-"] { white-space: pre !important; }
  </style>
  <% } %>
  ```

+ 代码块`js`添加

  ```bash
  在 themes\matery\source\libs\codeBlock目录下新建codeCopy.js文件
  ```

  ```javascript
  // 代码块一键复制(覆盖原内容)
  $(function () {
      var $copyIcon = $('<i class="fa fa-copy code_copy" title="复制代码" aria-hidden="true"></i>')
      var $notice = $('<div class="codecopy_notice"></div>')
      $('.code-area').prepend($copyIcon)
      $('.code-area').prepend($notice)
      // “复制成功”字出现
      function copy(text, ctx) {
          if (document.queryCommandSupported && document.queryCommandSupported('copy')) {
              try {
                  document.execCommand('copy') // Security exception may be thrown by some browsers.
                  $(ctx).prev('.codecopy_notice')
                      .text("复制成功")
                      .animate({
                          opacity: 1,
                          top: 30
                      }, 450, function () {
                          setTimeout(function () {
                              $(ctx).prev('.codecopy_notice').animate({
                                  opacity: 0,
                                  top: 0
                              }, 650)
                          }, 400)
                      })
              } catch (ex) {
                  $(ctx).prev('.codecopy_notice')
                      .text("复制失败")
                      .animate({
                          opacity: 1,
                          top: 30
                      }, 650, function () {
                          setTimeout(function () {
                              $(ctx).prev('.codecopy_notice').animate({
                                  opacity: 0,
                                  top: 0
                              }, 650)
                          }, 400)
                      })
                  return false
              }
          } else {
              $(ctx).prev('.codecopy_notice').text("浏览器不支持复制")
          }
      }
      // 复制
      $('.code-area .fa-copy').on('click', function () {
          var selection = window.getSelection()
          var range = document.createRange()
          range.selectNodeContents($(this).siblings('pre').find('code')[0])
          selection.removeAllRanges()
          selection.addRange(range)
          var text = selection.toString()
          copy(text, this)
          selection.removeAllRanges()
      })
  });
  ```

+ 代码块中的`{}`无法解析问题解决

  ```bash
  node_modules/hexo-prism-plugin/src/index.js文件中map里未支持大括号，补上以下内容后发现有效，在map中加上对应字符即可
  ```

  ```json
  // 需经过前面的步骤,不要直接来这里
  const map = {
    '&#39;': '\'',
    '&amp;': '&',
    '&gt;': '>',
    '&lt;': '<',
    '&quot;': '"',
    '&#123;': '{',	//添加的代码
    '&#125;': '}'		//添加的代码
  };
  ```

  