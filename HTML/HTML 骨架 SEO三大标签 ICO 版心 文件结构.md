---
title: HTML 骨架 SEO三大标签 ICO 版心 文件结构
date: 2022-07-17T19:55:09Z
lastmod: 2022-07-17T19:55:39Z
---

# HTML 骨架 SEO三大标签 ICO 版心 文件结构

# HTML 骨架

```html
<!DOCTYPE html> 
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
  
</body>
</html>
```

## 文档类型 DOCTYPE

文档类型声明, 用来告诉浏览器使用的html版本  
doctype写在第一行,不属于html标签

## 网页语言  lang

表示浏览器使用的语言  
方便搜索引擎分类, 浏览器翻译  
常见的取值有:zh-CN , en

## 网页字符集 charset

表示网页使用的字符集  
常见的有utf-8 gb2312 gbk  
开发中统一使用 utf-8

# SEO三大标签

SEO: 搜索引擎优化  
SEO的常见方法:

* 竞价排名
* 后缀改成html
* 标签语义化(在合适的地方使用合适的标签)

常见有语义的布局标签有哪些？

* header：网页头部
* nav：网页导航
* footer：网页底部
* aside：网页侧边栏
* section：网页区块
* article：网页文章

## SEO三大标签: title,description,keyword

title: 网页标题标签  
description: 网页描述标签  
keyword: 网页关键字标签

```html
    <title>这里是标题</title>
    <meta name="description" content="这里是描述">
    <meta name="keywords" content="这里是关键字">
```

# 设置ICO图标

使用link标签  
**    <linkrel="shortcut icon"href="favicon.ico"type="image/x-icon">**

# 版心

版心剧中,可以让盒子居中

```html
      .container{
          width: 1200px;
          margin: 0 auto;
      }
```

版心类常见命名: container wrapper w等

# 项目的文件结构

![image 1.png](assets/image 1-20220717195609-bit1kyc.png)
