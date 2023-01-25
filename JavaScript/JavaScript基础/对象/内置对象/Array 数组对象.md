---
title: Array 数组对象
date: 2022-07-17T20:51:02Z
lastmod: 2022-09-23T13:56:30Z
---

# Array 数组对象

# 创建数组对象的两种方式

利用数组字面量创建数组

利用new创建数组对象

# 检测是否为数组

## 使用 instanceof  运算符

instanceof ﻿可以判断原型是否处于原型链上

```JavaScript
        arr=[1,2,3];
        console.log(arr instanceof Array); //输出true
```

## 使用Array.isArray()方法

```JavaScript
        arr=[1,2,3];
        console.log(Array.isArray(arr)); //输出true
```

# 添加或删除数组元素

||||
| -------------------------| --------------------------------| ----------------------|
|方法名|说明|返回值|
|push(参数1, 参数2...)|末尾添加一个或多个元素|返回新的长度|
|pop()|删除数组末尾的元素|返回他删除的元素的值|
|unshift(参数1,参数2...)|向数组的开头添加一个或多个元素|返回新的长度|
|shift()|删除数组开头的元素|返回删除的元素的值|
|splice 删除数组内部元素|删除数组内部元素||

```JavaScript
            //修改数组元素
            // 添加元素的两个方法 push unshift
            var arr = new Array();
            arr = [1, 2, 3, 4];
            console.log(arr);

            console.log(arr.push("red", "apple")); //返回数组长度
            console.log(arr);

            console.log(arr.unshift("a", "b")); //返回数组长度
            console.log(arr);

            // 删除元素的两个方法 pop shift

            console.log(arr.pop()); //返回删除的元素
            console.log(arr);

            console.log(arr.shift()); //返回删除的元素
            console.log(arr);
```

![Snipaste_2022-07-17_20-51-27.png](assets/Snipaste_2022-07-17_20-51-27-20220717205129-tie98db.png)

# 数组排序

## reverse() 翻转数组

```JavaScript
            var arr=[1,2,3,4,5];
            arr.reverse();
            console.log(arr);
```

![Snipaste_2022-07-17_20-51-33.png](assets/Snipaste_2022-07-17_20-51-33-20220717205136-5gk5420.png)

## sort 数组排序

```JavaScript
            var arr = [2,1,5,4,3,7,5,6,2];
            arr.sort(compareFunction );
            console.log(arr);
```

![Snipaste_2022-07-17_20-51-41.png](assets/Snipaste_2022-07-17_20-51-41-20220717205144-5p18r9n.png)

### 注意:

* 如果不给sort传入参数, 那么默认把数组元素转换为字符串后按照Unicode排序
* 如果想要按照数组数字大小排序, 那么需要传入一个比较函数

### 比较函数

```JavaScript
            var arr = [21,1,5,43,3,7,55,6,2];
            arr.sort(function(a,b){
                // return a-b; //升序
                return b-a; //降序

            });
            console.log(arr);
```

注意:

* 如果没有指明`compareFunction` , 那么转换为字符串后按照Unicode排序
* 如果指明了 `compareFunction` ，那么数组会按照调用该函数的返回值排序。即 a 和 b 是两个将要被比较的元素：
* 如果 `compareFunction(a, b)` 小于 0 ，那么 a 会被排列到 b 之前；
* 如果 `compareFunction(a, b)` 大于 0 ， b 会被排列到 a 之前。

# 查找数组元素

## indexOf()

在数组中查找给定元素的第一个索引

## lastIndexOf()

在数组中查找给定元素的最后一个索引

```JavaScript
            var arr = [1, 2, 3, 4, 5, 5, 6];
            console.log(arr.indexOf(5));
            console.log(arr.lastIndexOf(5));
```

![Snipaste_2022-07-17_20-51-50.png](assets/Snipaste_2022-07-17_20-51-50-20220717205155-v8iwxw8.png)

## 注意:

* 如果查找不到, 那么返回-1

# 数组转换为字符串

## toString()

直接把数组转换为字符串, 没有参数, 以逗号分隔

## join("分隔符")

* 如果没有参数, 默认为逗号
* 如果想没有分隔符,可以使用`join("")`

没有参数时以逗号分隔, 可以传入参数作为自定义分隔符

```JavaScript
            var arr=["alpha", "beta", "charry"];
            console.log(arr.toString());
            console.log(arr.join());
            console.log(arr.join("-and-"));
```

![Snipaste_2022-07-17_20-52-01.png](assets/Snipaste_2022-07-17_20-52-01-20220717205205-3j5ttdh.png)

# concat连接数组

concat可以连接一个或多个数组

用法: 数组1 .concat(数组2,数组3.....)

```JavaScript
            var arr = ["alpha", "beta", "charry"];
            var arr1 = ["a", "b", "c"];
            var arr2= arr.concat(arr1);
            console.log(arr2);  //输出(6) ['alpha', 'beta', 'charry', 'a', 'b', 'c']
```

# slice 截取数组

用法: slice(开始下标,结束下标)

```JavaScript
            var arr=[1,2,3,4,5,6,7,8,9];
            var arr1=arr.slice(2,5);
            console.log(arr1); //输出(3) [3, 4, 5]
```

# splice 在指定位置删除或添加元素

用法`​ arr.splice(index,delCount[,item1,item2])`

index: 从哪开始添加或删除

delCount: 删除几个

item: 可选, 要添加的元素

```JavaScript
            var arr=[1,2,3,4,5,6,7,8,9];
            arr.splice(3,3);
            console.log(arr); //输出(6) [1, 2, 3, 7, 8, 9]

	var arr = ["red","blue","black"]
	删除blue并添加yellow
	arr.splice(1,1,"yellow")
```
