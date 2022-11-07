# this指向问题

## 目录

*   [全局作用域, 普通函数, 定时器](#全局作用域-普通函数-定时器)

*   [对象的方法](#对象的方法)

*   [事件](#事件)

*   [构造函数](#构造函数)

# 全局作用域, 普通函数, 定时器

在全局作用域, 普通函数, 定时器中, this指向window顶级对象,

```javascript
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

```javascript
o{
fun:function(){
  console.log(this);
}
}
o.fun() ; //输出的是o这个对象
```

# 事件

事件调用中的this指向绑定了事件的对象

```javascript
btn.onclick = function(){
  console.log(this); //输出btn, 因为btn绑定了这个事件
}
```

# 构造函数

构造函数中的this指向构造出来的那个对象

```javascript
var Person = function(name){
  console.log(this); //指向构造出来的对象
  this.name = name; //实际上与tim.name=name等价
} 
var tim = new Person("tim");
```
