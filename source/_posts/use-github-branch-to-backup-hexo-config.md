---
title: use github branch to backup hexo config
date: 2019-02-14 13:17:34
tags:
- github
- hexo
categories:
- Hexo
comments: true
description: github & hexo solution guidline
photos:
- "https://vu-1255958126.cos.ap-beijing.myqcloud.com/personal/vicky3.JPG"
#password: vicky
copyright: true
---
<script src="https://cdn.jsdelivr.net/npm/jquery/dist/jquery.min.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/font-awesome/css/font-awesome.min.css"/>
<script src="https://cdn.jsdelivr.net/gh/stevenjoezhang/live2d-widget/autoload.js"></script>

<script src="https://cdn.jsdelivr.net/gh/jackchenjy/balloon.js/balloon.min.js"></script>
>This is my first post.
>love vicky.

GitHub 分支备份hexo

# 创建分支目录

## 先新建一个hexo文件夹，作为分支的工作目录，用于保存将要备份的文件和文件夹
``$ mkdir hexo``

## 再把GitHub上的仓库clone到hexo文件夹
``$ git clone https://github.com/jackchenjy/jackchenjy.github.io hexo``

## 删除除了.git文件夹的其它所有文件和文件夹，得到版本管理的.git。下面命令不会删除隐藏文件和文件夹
``$ cd hexo``
``$ rm -r *``

## 最后把需要备份的文件和文件夹都复制到hexo文件夹下，hexo的目录结构应该如下
+ scaffolds/
+ source/
+ themes/
+ .git/
+ .gitignore
+ _config.yml
+ package.json

## 如果使用的主题是从GitHub克隆的，那么主题文件夹下有Git管理文件，需要将它们移除，我使用的是next，需要移除的文件如下
``$ rm -R themes/next/.git*``

# 创建分支

## 创建一个叫hexo的分支
``$ git checkout -b hexo``

## 保存所有文件到暂存区
``$ git add --all``

## 提交变更
``$ git commit -m "sys file backup"``

## 推送到GitHub，并用--set-upstream与origin创建关联，将hexo设置为默认分支
``$ git push --set-upstream origin hexo``

# 发表文章
## 新建Markdown文章，编辑文章
``$ hexo new test``

## 将相关更改推送到hexo分支
``$ git add .``
``$ git commit -m "发表文章test"``
``$ git push origin hexo``

## 将静态文件推送到master分支
``$ hexo clean # 如果配置文件没有更改，忽略该命令``
``$ hexo g -d``

## 写新文章并备份和部署
//进入hexo文件夹,应是hexo分支
```
git pull origin hexo //本地和远端的融合
hexo new post "new post name"  //写新文章
git add source
git commit -m "xxx"
git push origin hexo  //备份
hexo d -g  //部署
```

## 恢复hexo环境
前提:nodejs,git,hexo已经安装好，并配置好环境变量。
``git clone -b hexo git@github.com:jackchenjy/jackchenjy.github.io.git hexo //将Github中hexo分支clone到本地``
``cd hexo``
``npm install``
