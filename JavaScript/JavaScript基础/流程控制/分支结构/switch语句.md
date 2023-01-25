---
title: switch语句
date: 2022-07-17T21:07:57Z
lastmod: 2022-07-17T21:08:03Z
---

# switch语句

# switch语句

switch语句也是多分支语句, 它用于基于不同的条件来执行不同的代码, 当要针对变量设置一些类的特定值的选项时, 就可以使用switch

```JavaScript
switch(表达式){
  case value1;
    执行语句1;
    break;
  case value2;
    执行语句2;
    break;
   ....
   default: 默认语句; 
}
```

执行过程: 判断表达式的值, 找到相应的case语句, 执行对应的语句, 如果没有匹配的项, 那么就执行default语句

* 表达式一般为变量
* 判断case的时候是全等 "===" ,必须数据类型和值全部相等 比较运算符概述
* 如果当前case没有break ,那么不会退出switch ,会继续执行直到break或switch结束为止

# switch语句 和 if else if 多分支语句的区别

* 一般情况下, 这两个语句可以相互替换
* switch...case语句通常处理case为比较确定值的情况, 而if...else更加简洁, 常用于判断范围
* switch语句进行条件判断后直接执行语句, 效率更高, 而if...else有几个条件, 就要判断多少次
* 当分支比较少时, if...else语句的执行效率比switch语句高
* 当分支比较多时, switch语句的执行效率比较高, 而且结构更加清晰
