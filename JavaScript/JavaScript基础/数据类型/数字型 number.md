---
title: 数字型 number
date: 2022-07-17T21:19:20Z
lastmod: 2022-11-17T15:05:12Z
---

# 数字型 number

## 数字型 number

JS数字型既可以用来保存整数型, 也可以保存浮点型

```JavaScript
var age = 12;
var age = 12.222;
```

### 数字型进制

八进制: 0开始

十六进制: 0x开始

```JavaScript
//八进制 
var x=017;
//十六进制
var x=0x123abc;
```

### 数字型的最大值和最小值

利用一下代码可以输出数字型的最大值和最小值

```JavaScript
console.log(Number.MAX_VALUE);
console.log(Number.MIN_VALUE);

```

![Snipaste_2022-07-17_21-19-31.png](assets/Snipaste_2022-07-17_21-19-31-20220717211933-bymcd38.png)

### 数字型的三个特殊值

* infinity: 无穷大
* -infinity: 无穷小
* NaN: not a number, 代表非数字

  * NaN 指“不是一个数字”（not a number），NaN 是一个“警戒值”（sentinel value，有特殊用途的常规值），用于指出数字类型中的错误情况，即“执行数学运算没有成功，这是失败后返回的结果”。 `typeof NaN; // "number"`​ NaN 是一个特殊值，它和自身不相等，是唯一一个非自反（自反，reflexive，即 x === x 不成立）的值。而 `NaN !== NaN`​ 为 true。

### isNaN()方法

isNaN()可以用来判断一个变量是否是 非数字 , 返回true 或 false

![Snipaste_2022-07-17_21-19-38.png](assets/Snipaste_2022-07-17_21-19-38-20220717211941-76cb542.png)

‍
