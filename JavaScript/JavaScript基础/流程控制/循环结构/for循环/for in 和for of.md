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
