---
title: Yilia 相册实现有效解决
tags: Hexo
categories: Hexo
top: 5
cover: 'https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/Yilia.png'
abbrlink: 15944
date: 2020-10-19 20:42:42
top_img:
---

### 创建 `photos`

```javascript
E:\>cd 你的博客路径
E:\blog>cd source // 进入资源文件夹
E:\blog\source>hexo new page "photos" // 创建 photos
INFO  Created: E:\blog\source\photos\index.md 

***// 之后删除 source/photos/ index.md
    
```

###  创建 `Github`仓库:

![创建github仓库](https://img-blog.csdnimg.cn/2020101920485210.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)



### 克隆你的仓库至本地博客的根目录下:

![请在博客根目录下](https://img-blog.csdnimg.cn/20201019205449237.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)



#### 新建两个文件夹在你所克隆的仓库文件夹中: 

+ 新建文件夹并在两个文件夹下存放·`2014-11-16_name.jpg` 格式的图片(必须是此格式)

  ![新建两个文件夹](https://img-blog.csdnimg.cn/20201019205859490.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

  ```html
  
  开始只新建两个文件夹，分别是:
  
  	+ min_photos
  
  	+ photos
  
  ```
  

###  通过 `git` 命令对仓库远程关联

```bash

git add .

git commit -m "xxxx"

git branch -M main

git remote add origin xxx

git push -u origin main
                
```



### 下载网络上已知的样式:

![已知样式下载](https://img-blog.csdnimg.cn/20201019210552545.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)



### 在掘金发现这个解决方案很是重要:

```html

*** 注意: ***

	1. 修改: class= "instagram itemscope" 下的 href 路径

	2. 删除 photos 下的 dat.json

修改 index.ejs 的 href = "你的博客地址"

    <div class="instagram itemscope">
        <a href="https://chemlez.github.io/" target="_blank" class="open-ins">图片正在加载中…</a>
    </div>

```



### 修改 `修改ins.js文件里的render()函数`：

+ 先通过 `ipaddress`   解析出可加载的 `raw.xx.com` 的 `ip`, 将 `ip` 添加在 `hosts` 文件里

```python

ipaddress: https://www.ipaddress.com/

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201019211952623.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

+ `hosts`路径:

  ```python
   
   C:\Windows\System32\drivers\etc
          
   添加对应的 `ip`
  ```

  ![hosts路径](https://img-blog.csdnimg.cn/20201019212505974.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)



###  图片路径的获取:

```html

minSrc = 如下图

src = 如下图
```



![获取图片路径](https://img-blog.csdnimg.cn/20201019213247705.gif#pic_center)

### `python`脚本：

```python

将其中的.py文件拷贝至本地仓库blog-Picture文件夹中.  (跳转: 新建文件夹那一步查看 python 文件 )

根据脚本文件，图片的命名规则为：2019-10-21_xxx.jpg/png.

将图片[empty.png]下载放入博客目录下的 assets/img 文件夹中.

打开tool.py文件,修改def handle_photo():

    
    // 路径属于(source下) 删除的 data.json 处
    
    with open("E:/blog/source/photos/data.json", "w") as fp:
        
      
  -- 安装 python 所需要的两个模块可能出错

	我当初使用 windows + x : Windows PowerShell 到博客目录下使用: 
            
            pip install pillow (建议切换 pip 源下载 )
            
```



### 运行:

```bash

hexo clean

hexo g

hexo d

```



### 我的博客相册效果截图:

![效果截图](https://img-blog.csdnimg.cn/20201019214735290.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)



### 遗留问题:

+ 加入第二张图片时出现不了的解决方案

  ```python
  
  可能是 github 修改了 master --> main,提交命令导致
  
  所以修改 tool.py 的如下方法的 git 命令，注释掉原先的 git 命令,修改为最新的仓库关联方式
  
  def git_operation():
      
      os.system('git remote add origin https://github.com/lovobin/Blog-Back-Up.git')
      os.system('git branch -M main')
      os.system('git push -u origin main')
      '''
      git 命令行函数，将仓库提交
      
      ----------
      需要安装git命令行工具，并且添加到环境变量中
      '''
      #os.system('git add --all')
      #os.system('git commit -m "add photos"')
      #os.system('git push origin master')
  ```

  

+ 第二次的图片展示结果:
```python 
	
	首先得在博客本地执行一次 tool.py 

```
 ![正确显示二次提交的图片](https://img-blog.csdnimg.cn/20201020100626447.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

+ 分析过程来源：

```html
作者：ChmeLez
链接：https://juejin.im/post/6844904088878972941
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

具体参考: https://juejin.im/post/6844904088878972941
```