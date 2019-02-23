---
title: 卸载HEXO next 插件
date: 2019-02-22 22:26:52
tags:
- hexo
- 插件
categories:
- Hexo
comments: true
description: 卸载HEXO next Youku视频、live2d等插件
photos:
- "https://vu-1255958126.cos.ap-beijing.myqcloud.com/personal/vicky1.JPG"
---
首先删除\themes\next\layout下_layout.swig文件内的与youku和live2d有关的代码（你配置时添加的代码）
同理删除主题配置文件和hexo配置文件（如果也添加过live2d相关代码）。
检查是否页面还存在youku和live2d部件
将youku的npm安装命令
```
npm install -save hexo-tag-youku
```
换成
```
npm uninstall hexo-tag-youku -g
```
在你的hexo博客根目录执行。

将live2d的npm安装命令
```
npm install -save hexo-helper-live2d
```
稍作修改变为
```
npm uninstall hexo-helper-live2d -g
```
在你的hexo博客根目录执行。
清除本地浏览器缓存，输入命令“hexo s”部署，浏览器查看地址localhost：你的端口live2d部件是否还存在。
如果还存在，接着
直接文件管理器搜索”live2d“关键字，将hexo博客内所有含有”live2d“有关的文件夹全部删除。
测试插件已经不再显示了
