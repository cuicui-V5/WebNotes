---
title: vue3 - lazyload
date: 2023-01-14T15:48:43Z
lastmod: 2023-01-14T15:49:30Z
---

# vue3 - lazyload

实现图片懒加载

引入

```ts
import VueLazyLoad from "vue3-lazyload";
```

使用

```ts
app.use(VueLazyLoad, {
    loading:
        "https://picx.zhimg.com/v2-d7be5fcd1fb35461336a3db94ca1ff9c_xll.jpg?source=32738c0c",
    error:"xxx"
});
```
