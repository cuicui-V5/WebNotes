---
title: Express
date: 2022-09-01T10:36:29Z
lastmod: 2022-09-01T13:54:02Z
---

# Express

# 简介

Express是基于Node.js平台的, 快速, 开放, 极简的Web开发框架

Express的作用和Node.js内置的`http`模块类似, 是专门用来创建Web服务器的

本质: 就是一个npm的第三包 提供了快速创建Web服务器的便捷方法

# Express能做什么

使用Express,我们可以方便, 快速的创建Web服务器和Api服务器

# 安装

```powershell
npm i express
```

# 创建一个服务器

```js
// 导入express
const express = require("express");
// 创建服务器
const server = express();
// 开启服务器
server.listen(80, () => {
    console.log("server started at http://127.0.0.1");
});
```
