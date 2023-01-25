---
title: this指向问题
date: 2022-07-17T21:35:07Z
lastmod: 2022-07-17T21:35:15Z
---

# this指向问题

一般情况下, this指向的一般是调用它的那个对象

# 全局作用域, 普通函数, 定时器

在全局作用域, 普通函数, 定时器中, this指向window顶级对象,

```JavaScript
console.log(this) ; //输出window
function fun(){
  console.log(this);
}
fun(); //输出window
window.setTimeout(function(){
  console.log(this); //仍然输出window
},1000)
```

# 对象的方法

对象方法中的this指向该对象

```JavaScript
o{
fun:function(){
  console.log(this);
}
}
o.fun() ; //输出的是o这个对象
```

# 事件

事件调用中的this指向绑定了事件的对象

```JavaScript
btn.onclick = function(){
  console.log(this); //输出btn, 因为btn绑定了这个事件
}
```

# 构造函数

构造函数中的this指向构造出来的那个对象

```JavaScript
var Person = function(name){
  console.log(this); //指向构造出来的对象
  this.name = name; //实际上与tim.name=name等价
} 
var tim = new Person("tim");
```
