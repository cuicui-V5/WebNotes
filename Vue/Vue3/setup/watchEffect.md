# watchEffect

立即运行一个函数，同时响应式地追踪其依赖，并在依赖更改时重新执行。

函数中用到的数据在更改时会重新执行其回调

注意, 调用`ref`​中的数据时, 需要使用`.value`​, `reactive`​不需要

```js
        watchEffect(() => {
            console.log("数字改变了", num1.value, num2.value, num3.value, num4.value);
            console.log("数字改变了", p.name, p.age);
        });
```
