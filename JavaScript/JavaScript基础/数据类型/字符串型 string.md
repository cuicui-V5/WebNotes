---
title: 字符串型 string
date: 2022-07-17T21:19:07Z
lastmod: 2022-07-17T21:19:13Z
---

# 字符串型 string

## 字符串型 string

字符串型可以是引号内的任意文本, 可以为双引号""或单引号''

```JavaScript
var str="abc"; //双引号
var str='abc' //单引号

常见错误 不加引号
var str=abc;
```

因为html的标签使用的是双引号, 所以JS推荐使用单引号

### 字符串引号嵌套

JS可以单引号嵌套双引号, 或者双引号嵌套单引号

```JavaScript
正确写法
var str="我是'abc'"; //双引号嵌套单引号
var str='我是"abc"'; //单引号嵌套双引号

错误写法
var str="我是"abc"def"; //全部使用双引号
var str='我是'abc'def'; //全部使用单引号
var str="我是abc'; //单双引号混用
```

### 转义字符

|||
| ----------| --------------------|
|转义字符|含义|
|\n|换行符. n是newline|
||斜杠|
|'|单引号'|
|"|双引号"|
|\t|tab缩进|
|\b|空格, b是blank|

### 字符串长度 length

通过字符串.length可以输出字符串的长度

```JavaScript
var v = prompt("请输入");
console.log(v.length);
```

### 字符串拼接 +

* 可以使用+进行字符串拼接., 字符串+任意类型 = 新字符串
* 拼接会把与字符串相加的任何类型转换成字符串型, 然后再拼接

```JavaScript
console.log("abc"+123); //输出abc123
console.log(123+"abc"); //输出123+abc

```

# 模板字符串 es6

使用模板字符串允许你在字符串中轻松嵌入变量而不用字符串拼接

在反引号````中定义字符串, 使用`${ } ​`表示变量即可

```JavaScript
            var a=100;
            var b=200;

            console.log(`用反引号包裹的叫做模板字符串${a} ${b}`);
```
