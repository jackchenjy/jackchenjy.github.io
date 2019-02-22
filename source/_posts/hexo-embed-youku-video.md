---
title: Hexo在文章中插入Youku视频
date: 2019-02-22 20:26:29
tags:
- 优酷
- hexo
categories:
- Hexo
comments: true
description: Hexo在文章中插入Youku视频
photos:
- "http://aixti.cn/wp-content/uploads/2019/01/IMG_3469-1.jpg"
---
安装 hexo-tag-youku插件，在文章中插入Youku视频

```
npm install --save hexo-tag-youku
```

使用方式

```
{% youku height width %}
优酷视频id
{% endyouku %}
```
