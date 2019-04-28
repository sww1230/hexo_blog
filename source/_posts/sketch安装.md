---
title: sketch设计软件安装及插件配置
date: 2019-04-28
tags: sketch
---

### sketch软件安装
  1. [下载地址](https://xclient.info/s/sketch.html?t=ab9fbba422e9a35053ba43c79f13cf357df439d5)
  2. 如果提示软件有损，请先运行：

     ````
      sudo spctl --master-disable
     ````
 
### 汉化插件
  1. SketchI18N.sketchplugin

### 图标字体：

  #### 一、安装字体插件

  1. 下载并解压：sketch-iconfont-master.zip
  2. 双击 iconfont.sketchplugin 完成安装


  #### 二、安装 Font Bundle

  >安装好 Sketch Iconfont 之后，你会发现，这个 Plugin，还不能使用。既然是管理 IconFont 的 Plugin，第一件事情就是要先安装 IconFont，然后才能进行管理。Plugin 的作者为了方便使用，提供了一个 Font Bundle， 里面包括了多个比较热门的 IconFont，安装后就可以使用了。

  1. 下载并解压： font-bundles-master.zip
  2. 打开 ttf-files 文件夹，依次安装里面的字体
  3. 打开 Sketch，点击 Plugins -> Icon Font -> Install a Font-Bundle
  4. 在弹出的对话框中，选择 font-bundles-master 文件夹，然后点击 Open


  
### 输出html标注页面

  1. sketch-measure-master