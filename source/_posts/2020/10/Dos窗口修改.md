---
title: Dos窗口修改
tags:
  - 电脑小技巧
cover: 'https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/dos.png'
abbrlink: 2867
date: 2020-10-21 00:04:46
top_img:
---

```bash


Windows Registry Editor Version 5.00 
[HKEY_CURRENT_USER\Console\%SystemRoot%_system32_cmd.exe] 
"WindowSize"=dword:00190069 
"ScreenBufferSize"=dword:01170058 
"WindowPosition"=dword:0079004b 
"ColorTable01"=dword:00235600 
"FontSize"=dword:00160010 
"FontWeight"=dword:00000190 
"FaceName"="Consolas" 
"FontFamily"=dword:00000036

保存为: Consolas.reg

双击运行

修改 cmd 属性的透明度为: 85%

```

### 运行 `Ipython`:

![改善Doc](https://img-blog.csdnimg.cn/20201021001947816.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)



###  Vscode默认终端修改:

+ 修改为`bash`

  ![](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/shellConfig.png)

+ 添加配置

  > ```bash
  >    "terminal.integrated.shell.windows": "D:\\Program Files\\Git\\bin\\bash.exe", #改为你的路径
  > ```

+ 主题色自选

  > 主题色: https://glitchbone.github.io//vscode-base16-term/#/bright

+ 添加颜色配置，点击`Copy to clipboard`

  > ```bash
  > "workbench.colorCustomizations": {
  >     "terminal.background":"#000000",
  >     "terminal.foreground":"#E0E0E0",
  >     "terminalCursor.background":"#E0E0E0",
  >     "terminalCursor.foreground":"#E0E0E0",
  >     "terminal.ansiBlack":"#000000",
  >     "terminal.ansiBlue":"#6FB3D2",
  >     "terminal.ansiBrightBlack":"#B0B0B0",
  >     "terminal.ansiBrightBlue":"#6FB3D2",
  >     "terminal.ansiBrightCyan":"#76C7B7",
  >     "terminal.ansiBrightGreen":"#A1C659",
  >     "terminal.ansiBrightMagenta":"#D381C3",
  >     "terminal.ansiBrightRed":"#FB0120",
  >     "terminal.ansiBrightWhite":"#FFFFFF",
  >     "terminal.ansiBrightYellow":"#FDA331",
  >     "terminal.ansiCyan":"#76C7B7",
  >     "terminal.ansiGreen":"#A1C659",
  >     "terminal.ansiMagenta":"#D381C3",
  >     "terminal.ansiRed":"#FB0120",
  >     "terminal.ansiWhite":"#E0E0E0",
  >     "terminal.ansiYellow":"#FDA331"
  > },
  > ```

+ 效果预览

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/colorVscode.png" width="600">

+ `Vscdoe`实际效果偏差较大不是很理想