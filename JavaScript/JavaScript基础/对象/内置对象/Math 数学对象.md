---
title: Math 数学对象
date: 2022-07-17T20:49:03Z
lastmod: 2022-07-17T20:49:14Z
---

# Math 数学对象

Math对象不是构造函数, 它具有数学常数和函数的属性和方法, 跟数学相关的运算(求绝对值, 取整, 最大值)等可以使用Math中的成员

||||
| ----------------------------| --------------------| -----------------------------------------------------------------------------------|
|成员|作用|注意|
|Math.PI|圆周率||
|Math.floor()|向下取整||
|Math.ceil()|向上取整||
|Math.round()|四舍五入|Math.round(-3.5 )=-3    .5往大了取|
|Math.abs()|绝对值|具有隐式转换, 会把字符串型转换成数字型, 如果有非数字类型或者参数为空, 那么输出NaN|
|Math.max( 参数1, 参数2...)|输出参数中的最大值|如果有非数字类型 ,那么返回NaN     , 如果没有任何参数,  那么返回-infinity|

## 随机数方法random

random()方法返回一个随机的小数 在0-1之间 ( 不包括1 )

random方法没有参数

```JavaScript
        // 得到0-1之间的随机数
        console.log(Math.random());

        //得到两数之间的随机数
        var randomNum = function (min, max) {
            var num;
            num = Math.random() * (max - min) + min;
            return num;
        };
        console.log(randomNum(1, 10));

        //两数之间的随机整数 包括min, 但不包括max
        var randomInt = function (min, max) {
            var num;
            min = Math.ceil(min);
            max = Math.floor(max);
            num = Math.floor(Math.random() * (max - min) + min);
            return num;

        }; //包括min, 但不包括max
        console.log(randomInt(1, 10));


        //两数之间的随机整数 包括min, 也包括max
        var randomInt = function (min, max) {
            var num;
            min = Math.ceil(min);
            max = Math.floor(max);
            num = Math.floor(Math.random() * (max - min + 1) + min);
            return num;

        }; //包括min, 也包括max
        console.log(randomInt(1, 10));
```
