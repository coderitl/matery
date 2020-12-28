---
title: Hexo-Gulp优化加载
date: 2020-12-28 14:45:41
tags: 
- Hexo
- 加载优化
- matery
categories: matery-theme
---

###  加载优化<!-- more -->

+ 插件安装

  ```bash
  # 全局安装gulp模块
  npm install gulp -g
  # 安装各种小功能模块  执行这步的时候，可能会提示权限的问题，最好以管理员模式执行
  npm install gulp gulp-htmlclean gulp-htmlmin gulp-minify-css gulp-uglify gulp-imagemin --save
  # 额外的功能模块
  npm install gulp-debug gulp-clean-css gulp-changed gulp-if gulp-plumber gulp-babel babel-preset-es2015 del @babel/core --save
  
  ```

+ 新建文件

  ```bash
   在Hexo根目录新建文件 gulpfile.js，并复制以下内容到文件中，有中文注释，可以根据自己需求修改。
   
   注意：文件名不能错，一定为 gulpfile.js，否则会出错！
  ```

  ```javascript
  var gulp = require("gulp");
  var debug = require("gulp-debug");
  var cleancss = require("gulp-clean-css"); //css压缩组件
  var uglify = require("gulp-uglify"); //js压缩组件
  var htmlmin = require("gulp-htmlmin"); //html压缩组件
  var htmlclean = require("gulp-htmlclean"); //html清理组件
  var imagemin = require("gulp-imagemin"); //图片压缩组件
  var changed = require("gulp-changed"); //文件更改校验组件
  var gulpif = require("gulp-if"); //任务 帮助调用组件
  var plumber = require("gulp-plumber"); //容错组件（发生错误不跳出任务，并报出错误内容）
  var isScriptAll = true; //是否处理所有文件，(true|处理所有文件)(false|只处理有更改的文件)
  var isDebug = true; //是否调试显示 编译通过的文件
  var gulpBabel = require("gulp-babel");
  var es2015Preset = require("babel-preset-es2015");
  var del = require("del");
  var Hexo = require("hexo");
  var hexo = new Hexo(process.cwd(), {}); // 初始化一个hexo对象
  
  // 清除public文件夹
  gulp.task("clean", function () {
      return del(["public/**/*"]);
  });
  
  // 下面几个跟hexo有关的操作，主要通过hexo.call()去执行，注意return
  // 创建静态页面 （等同 hexo generate）
  gulp.task("generate", function () {
      return hexo.init().then(function () {
          return hexo
              .call("generate", {
                  watch: false
              })
              .then(function () {
                  return hexo.exit();
              })
              .catch(function (err) {
                  return hexo.exit(err);
              });
      });
  });
  
  // 启动Hexo服务器
  gulp.task("server", function () {
      return hexo
          .init()
          .then(function () {
              return hexo.call("server", {});
          })
          .catch(function (err) {
              console.log(err);
          });
  });
  
  // 部署到服务器
  gulp.task("deploy", function () {
      return hexo.init().then(function () {
          return hexo
              .call("deploy", {
                  watch: false
              })
              .then(function () {
                  return hexo.exit();
              })
              .catch(function (err) {
                  return hexo.exit(err);
              });
      });
  });
  
  // 压缩public目录下的js文件
  gulp.task("compressJs", function () {
      return gulp
          .src(["./public/**/*.js", "!./public/libs/**"]) //排除的js
          .pipe(gulpif(!isScriptAll, changed("./public")))
          .pipe(gulpif(isDebug, debug({ title: "Compress JS:" })))
          .pipe(plumber())
          .pipe(
              gulpBabel({
                  presets: [es2015Preset] // es5检查机制
              })
          )
          .pipe(uglify()) //调用压缩组件方法uglify(),对合并的文件进行压缩
          .pipe(gulp.dest("./public")); //输出到目标目录
  });
  
  // 压缩public目录下的css文件
  gulp.task("compressCss", function () {
      var option = {
          rebase: false,
          //advanced: true, //类型：Boolean 默认：true [是否开启高级优化（合并选择器等）]
          compatibility: "ie7" //保留ie7及以下兼容写法 类型：String 默认：''or'*' [启用兼容模式； 'ie7'：IE7兼容模式，'ie8'：IE8兼容模式，'*'：IE9+兼容模式]
          //keepBreaks: true, //类型：Boolean 默认：false [是否保留换行]
          //keepSpecialComments: '*' //保留所有特殊前缀 当你用autoprefixer生成的浏览器前缀，如果不加这个参数，有可能将会删除你的部分前缀
      };
      return gulp
          .src(["./public/**/*.css", "!./public/**/*.min.css"]) //排除的css
          .pipe(gulpif(!isScriptAll, changed("./public")))
          .pipe(gulpif(isDebug, debug({ title: "Compress CSS:" })))
          .pipe(plumber())
          .pipe(cleancss(option))
          .pipe(gulp.dest("./public"));
  });
  
  // 压缩public目录下的html文件
  gulp.task("compressHtml", function () {
      var cleanOptions = {
          protect: /<\!--%fooTemplate\b.*?%-->/g, //忽略处理
          unprotect: /<script [^>]*\btype="text\/x-handlebars-template"[\s\S]+?<\/script>/gi //特殊处理
      };
      var minOption = {
          collapseWhitespace: true, //压缩HTML
          collapseBooleanAttributes: true, //省略布尔属性的值 <input checked="true"/> ==> <input />
          removeEmptyAttributes: true, //删除所有空格作属性值 <input id="" /> ==> <input />
          removeScriptTypeAttributes: true, //删除<script>的type="text/javascript"
          removeStyleLinkTypeAttributes: true, //删除<style>和<link>的type="text/css"
          removeComments: true, //清除HTML注释
          minifyJS: true, //压缩页面JS
          minifyCSS: true, //压缩页面CSS
          minifyURLs: true //替换页面URL
      };
      return gulp
          .src("./public/**/*.html")
          .pipe(gulpif(isDebug, debug({ title: "Compress HTML:" })))
          .pipe(plumber())
          .pipe(htmlclean(cleanOptions))
          .pipe(htmlmin(minOption))
          .pipe(gulp.dest("./public"));
  });
  
  // 压缩 public/medias 目录内图片
  gulp.task("compressImage", function () {
      var option = {
          optimizationLevel: 5, //类型：Number 默认：3 取值范围：0-7（优化等级）
          progressive: true, //类型：Boolean 默认：false 无损压缩jpg图片
          interlaced: false, //类型：Boolean 默认：false 隔行扫描gif进行渲染
          multipass: false //类型：Boolean 默认：false 多次优化svg直到完全优化
      };
      return gulp
          .src("./public/medias/**/*.*")
          .pipe(gulpif(!isScriptAll, changed("./public/medias")))
          .pipe(gulpif(isDebug, debug({ title: "Compress Images:" })))
          .pipe(plumber())
          .pipe(imagemin(option))
          .pipe(gulp.dest("./public"));
  });
  // 执行顺序： 清除public目录 -> 产生原始博客内容 -> 执行压缩混淆 -> 部署到服务器
  gulp.task(
      "build",
      gulp.series(
          "clean",
          "generate",
          "compressHtml",
          "compressCss",
          "compressJs",
          "compressImage",
          gulp.parallel("deploy")
      )
  );
  
  // 默认任务
  gulp.task(
      "default",
      gulp.series(
          "clean",
          "generate",
          gulp.parallel("compressHtml", "compressCss", "compressJs","compressImage")
      )
  );
  //Gulp4最大的一个改变就是gulp.task函数现在只支持两个参数，分别是任务名和运行任务的函数
  
  ```

  ###  执行方式有两种：

  - 直接在`Hexo`根目录执行 `gulp`或者 `gulp default` ，这个命令相当于 `hexo cl&&hexo g` 并且再把代码和图片压缩。
  - 在`Hexo`根目录执行 `gulp build` ，这个命令与第1种相比是：在最后又加了个 `hexo d` ，等于说生成、压缩文件后又帮你自动部署了。

  >  值得注意的是：这个加入了图片压缩，如果不想用图片压缩可以把第154行的 `"compressImage",` 和第165行的 `,"compressImage"` 去掉即可

  

