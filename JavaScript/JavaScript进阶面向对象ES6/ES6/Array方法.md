# Array方法

# 构造函数方法Array.from()

将类数组或可遍历对象转换为真正的数组

```js
let arrayLike = {
    0: "tim",
    1: "joke",
    2: "mom",
    length: 3
}

let arr = Array.from(arrayLike)
console.log(arr);
```

Array.from()还可以接受第二个参数, 第二个参数为处理函数, 用于对数据进行处理

第二个参数为处理函数, 参数为数组成员, 返回值为处理后的值

```js
let arrayLike = {
    0: "tim",
    1: "joke",
    2: "mom",
    length: 3
}

let arr = Array.from(arrayLike, item =>item+"处理")
console.log(arr);
```

# 查找实例方法 `find()` /`findIndex()`

语法:

 `arr.find(callback(item,index))`

`arr.findIndex(callback(item,index))​`

参数: 

`item ​`: 当前的数组成员 

`index`: 当前的数组下标

‍

`find`方法返回第一个回调函数返回值为真的数组成员

`findIndex`方法返回第一个回调函数返回值为真的数组成员的==下标==

‍

```js
let arr = [
    {
        name: "tim",
        age: 18,
    },
    {
        name: "jack",
        age: 10,
    },
];
console.log(arr.find(item=>item.name=="jack")); //{name: 'jack', age: 10}
console.log(arr.findIndex(item=>item.name=="jack")); //1
```

# 判断数组内部是否有元素

语法: `arr.includes(元素)`

如果数组内部含有指定元素, 那么返回`true`, 如果没有, 返回`false`

```js
let arr= [1,2,3,4,5,6,7,8,9]
console.log(arr.includes(1)); //true
console.log(arr.includes(0)); //false
```

‍

# reduce方法

语法: `arr.reduce((pre,current)=>{},initVal)`​

参数: 

* ​`pre`​ :上次迭代的结果
* ​`current`​: 当前迭代的值
* ​`initVal`​: 初始值

执行过程: `reduce`​方法会迭代数组内所有值, 并且会把上次`return`的执行结果作为当前的`pre`​参数

注意: `reduce`中一定要使用`return`返回值

```js
// 累加值
let arr = [1, 2, 3, 4, 5];

let res = arr.reduce((sum, val) => {
    sum += val;
    return sum;
}, 0);
console.log(res);

// 拼合字符串
let arr2 = ["小明", "小红", "小强"];

let res2 = arr2.reduce((sum, val) => {
    sum += val;
    return sum;
}, "");
console.log(res2);

// 求每个人的年龄和

let arr3 = [
    {
        name: "小明",
        age: 20,
    },
    {
        name: "小hs",
        age: 30,
    },
    {
        name: "小a",
        age: 50,
    },
];

let res3 = arr3.reduce((sum, val) => {
    sum += val.age;
    return sum;
}, 0);
console.log(res3);

```
