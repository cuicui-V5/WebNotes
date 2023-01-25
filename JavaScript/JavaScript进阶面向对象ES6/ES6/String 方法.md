---
title: String 方法
date: 2022-08-03T10:08:45Z
lastmod: 2022-08-03T10:21:19Z
---

# String 方法

# startsWith()和endsWith()方法

`startsWith() ​`和 `endsWith()` 方法可以检测字符串是否以指定的参数开头或结尾

语法: 

`startsWith("str")`

`endsWith("str")`

‍

```js
let str = "hello world!";
let r1 = str.startsWith("he");
let r2 = str.startsWith("He");
let r3 = str.endsWith("!");
let r4 = str.endsWith("?");
console.log(r1, r2, r3, r4);
```

![Snipaste_2022-08-03_10-17-24](assets/Snipaste_2022-08-03_10-17-24-20220803101726-wk4tzi0.png)​

‍

# repeat() 方法

使用repeat()方法可以返回重复指定次数的新字符串

`str.repeat(次数);`

‍

```js
let str = "hello World! ";
let str2 = str.repeat(5);
console.log(str2); //hello World! hello World! hello World! hello World! hello World! 
```
