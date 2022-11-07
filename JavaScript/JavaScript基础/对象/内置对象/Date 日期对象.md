# Date 日期对象

Date日期对象是一个构造函数, 必须使用new 调用创建日期对象 利用构造函数创建对象

* Data和Math 数学对象不一样,他是一个构造函数, 需要实例化后才能使用
* Data实例用来处理日期与时间
* Data对象基于1970-01-01世界标准时间起的毫秒数

# Date对象的使用

## 使用Data对象必须实例化

`var data = new Data();`

## 无参数直接调用

```JavaScript
        var date = new Date();
        console.log(date);
```

没有参数直接调用, 返回当前系统的时间

![Snipaste_2022-07-17_20-52-36.png](assets/Snipaste_2022-07-17_20-52-36-20220717205238-rkbm7ng.png)

## 初始化参数

### 数字型

`2022,10,01 年,月,日`

注意:

* 月份从0开始

```JavaScript
        var date1 = new Date(2022,10,1);
        console.log(date1); //输出Tue Nov 01 2022 00:00:00 GMT+0800 (中国标准时间) 
        //实际输出11月

```

![Snipaste_2022-07-17_20-52-45.png](assets/Snipaste_2022-07-17_20-52-45-20220717205247-b6qdacc.png)

### 字符串型

"2022-10-01 9:9:9"

```JavaScript
        var date2 = new Date("2022-10-01 9:9:9");
          console.log(date2); //输出Sat Oct 01 2022 09:09:09 GMT+0800 (中国标准时间)

```

![Snipaste_2022-07-17_20-52-58.png](assets/Snipaste_2022-07-17_20-52-58-20220717205302-idboi98.png)

# 常用属性方法

||||
| ----------------------------------| --------------------------------| --------------------|
|属性和方法|说明|注意|
|getFullYear()|获取年份||
|getMonth()|获取月份|从0开始|
|getDay()|获取星期几|周日是0|
|getDate()|获取当前的日期||
|getHours()|获取当前小时||
|getMinutes()|获取当前分钟||
|getSeconds()|获取当前秒钟||
|以上这些get方法还有对应的set方法|设置时间||
|valueOf()|从1970-01-01到对象时间的毫秒数||
|getTime()|从1970-01-01到对象时间的毫秒数||
|Date.now()|从1970-01-01到当前的毫秒数|注意Date没有小括号|
||||

```JavaScript
        var date2 = new Date("2022-10-01 9:9:9");
        console.log(date2.getFullYear());
        console.log(date2.getMonth());
        console.log(date2.getDay());
        console.log(date2.getDate());
        console.log(date2.getHours());
        console.log(date2.getMinutes());
        console.log(date2.getSeconds());
```

## +new Date() 获取时间戳

`console.log(+new Date());` 也可使获取到对象时间的时间戳
