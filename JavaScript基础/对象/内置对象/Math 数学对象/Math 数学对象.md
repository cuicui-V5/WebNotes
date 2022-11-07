# Math 数学对象

## 目录

*   [随机数方法random](#随机数方法random)

## 随机数方法random

random()方法返回一个随机的小数 在0-1之间 ( 不包括1 )

random方法没有参数

```javascript
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
