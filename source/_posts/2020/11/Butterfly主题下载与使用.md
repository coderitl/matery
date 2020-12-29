---
title: Butterfly主题下载与使用
tags: theme
cover: 'https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/buff.png'
abbrlink: 35587
date: 2020-11-13 14:10:28
top_img:
---

###  Butterfly

```bash
1. 进入 Butterfl git 主题页

	https://github.com/jerryc127/hexo-theme-butterfly -- 操作链接

2. 阅读 README.md 

3. 主要进行如下操作:

	克隆稳定版本: git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
	
	安装: npm i hexo-theme-butterfly (使用 dos 窗口下载,别用gitbash here 的 Terminology)
			
	     npm install hexo-renderer-pug hexo-renderer-stylus( 保此错误使用 If you don't have pug & stylus renderer, try this，建议提前安装，后续不会出现)
	
	修改博客根目录下的: _config.yml
	
		theme: butterfly
		
4. 执行 Hexo 命令:

	hexo clean
	
	hexo g
	
	hexo d
	
```





###  Butterfly预览:

+ `Butterfly `推荐理由

  > + 支持`markdown`代码语法高亮,模块舒适

  ​	<img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/Butterfly.png" width="700">

  > + 支持夜间模式

  > + 支持分页，无需个人配置

  ​	<img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/fenye.png">

  > + 全屏阅读

  ​	<img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/Emax.png" alt="全屏阅读">

  

+ 代码块配置(其余参数没必要尝试，效果没有)

  > ```css
  > highlight_theme: mac(推荐) / mac light
  > ```

  + `mac`

    ![highlight_theme: mac](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/mac.png)

  + `mac light`

    ​	<img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/macLight.png" width="700">

+ 友情链接显示效果极度舒服

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/friends.png" width="700">

  

###  背景修改:

> 主题下的 `_cconfig.yml`
>
> `index_img:`
>
> ​	·····

​	

###   文章左或右图片显示:

> 文章顶部添加:
>
> ​	top_img:
>
> ​	cover: 图片链接
>
> 



###  修改文章封皮显示图片:

![图片配置](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/topImgC.png)



###  中文化侧边栏:

+ 在根目录下的` _config.yml` 文件中:

  > ```bash
  > language: zh-CN
  > ```

![中文化侧边栏](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/siderbar.png)

###  github代码提交集成图的添加:

> <a href="https://github.com/Zfour/Butterfly-gitcalendar">效果出处与配置方案</a>(请点击)





> ##  本小站具体效果在主题官方文档皆可实现,请初遇问题细心，再细心阅读
>
> ##  官方文档!!!!   查阅总有不一样的记忆!!!



```html
个人联系方式: 
	
	QQ: 3327511395

	QQ邮箱:  3327511395@qq.com(QQ有推送查阅及时!)

	Google邮箱: aidou6942@gmail.com(未登录,不能及时查看)

```



###   `_posts`文章头信息修改:

```bash
站点(`scaffolds`)目录下 `post.md`:

# 可以添加任何存在切你想要出现的配置
```

+ 效果演示

  ![文章头配置信息的添加](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/HeadConfig.png)

###  文章密码:

> 
>
> 加密文章密码暂时统一为: `hexo`
>
> 

