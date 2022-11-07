# provide 与 inject

![Snipaste_2022-11-05_15-04-26](assets/Snipaste_2022-11-05_15-04-26-20221105150451-tk3chjj.png)​

一种祖孙间通信方式

在祖先组件中使用`provide`​提供数据, 在后代组件中使用`inject`​使用数据

```js
// 祖先组件
provide("person", person);

// 后代组件
let person = inject("person");

console.log(person);
```

‍
