---
title: JavaScript
date: 2022-08-04T09:14:46Z
lastmod: 2022-11-17T14:15:19Z
---

# JavaScript

异步加载

```js
<script src="index.js"></script>
//浏览器必须等待 index.js 加载和执行完毕才能去做其它事情。

<script async src="index.js"></script>
//index.js 的加载是异步的，加载时不会阻塞浏览器做任何其它的事情。
//当它加载结束，JS 脚本会立即执行。

<script defer src="index.js"></script>
//JS 的加载是异步的，执行是被推迟的。
//使用了 defer 标记的脚本文件，会等整个文档解析完成，在 DOMContentLoaded 事件触发之前执行
```
