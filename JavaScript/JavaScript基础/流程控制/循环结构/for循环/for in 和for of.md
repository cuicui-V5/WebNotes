---
title: for in 和for of
date: 2022-07-19T13:04:33Z
lastmod: 2022-07-19T13:06:15Z
---

# for in 和for of

这两种循环主要用于对象

```js
        let arr = [1,2,3,4,5];
        console.log(arr);
        for (const iterator of arr) {
            console.log(iterator);
        } //输出值
        for (const key in arr) {
          console.log(key);
        }//输出下标
```

‍
