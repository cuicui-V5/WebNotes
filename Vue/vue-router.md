---
title: vue-router
date: 2022-10-25T14:55:22Z
lastmod: 2022-10-26T10:05:19Z
---

# vue-router

vue-router 是 vue 的一个插件库, 专门用来实现 SPA 应用

# SPA 应用

SPA(single page web application)应用, 又叫单页应用, 整个应用只有一个完整的页面, 点击页面中的导航链接不会刷新页面, 只会做页面的局部更新, 数据需要通过 ajax 请求获取

‍

# 路由

一个路由就是一组(key:value)的映射关系, `key` ​为路径, `value` ​可能为 `function` ​或 `component`​

### 路由的分类

后端路由:

* ​`value` ​是 `function`​, 用于处理客户端提交的请求
* 工作过程: 服务器接收到一个请求时, 根据请求路径找到匹配的处理函数来返回相应的数据

前端路由:

* ​`value` ​是 `component`​, 用于展示页面内容
* 工作过程, 当浏览器的路径改变时, 对应的组件就会显示

‍
