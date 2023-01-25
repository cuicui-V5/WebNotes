---
title: watch
date: 2022-11-03T15:46:29Z
lastmod: 2022-11-03T16:56:50Z
---

# watch

# 侦听器 watch

语法: `watch(target,handler,option)`​

* 当`target`​是`ref`​对象时, 可以正常获取`oldValue`​, 但是`reactive`​对象不能
* 如果需要监视多个数据, 那么将数据放入数组内即可
* 如果监视`reactive`​对象, 那么强制开启了深度监视, `deep`​配置项无效
* 如果需要监视`reactive`​对象内的某个属性, 那么需要把该属性放入函数内 `() => person.name`​, 此时也可以用数组

# watchEffect

立即运行一个函数，同时响应式地追踪其依赖，并在依赖更改时重新执行。

函数中用到的数据在更改时会重新执行其回调

注意, 调用`ref`​​中的数据时, 需要使用`.value`​​, `reactive`​​不需要

```js
        watchEffect(() => {
            console.log("数字改变了", num1.value, num2.value, num3.value, num4.value);
            console.log("数字改变了", p.name, p.age);
        });
```

### `watch`​ vs. `watchEffect`​

​`watch`​ 和 `watchEffect`​ 都能响应式地执行有副作用的回调。它们之间的主要区别是追踪响应式依赖的方式：

* ​`watch`​ 只追踪明确侦听的数据源。它不会追踪任何在回调中访问到的东西。另外，仅在数据源确实改变时才会触发回调。`watch`​ 会避免在发生副作用时追踪依赖，因此，我们能更加精确地控制回调函数的触发时机。
* ​`watchEffect`​，则会在副作用发生期间追踪依赖。它会在同步执行过程中，自动追踪所有能访问到的响应式属性。这更方便，而且代码往往更简洁，但有时其响应性依赖关系会不那么明确。

## 后置刷新的watch

如果想在侦听器回调中能访问被 Vue 更新**之后**的DOM，你需要指明 `flush: 'post'`​ 选项：

‍

```js
watch(source, callback, {
  flush: 'post'
})

watchEffect(callback, {
  flush: 'post'
})
```

后置刷新的 `watchEffect()`​ 有个更方便的别名 `watchPostEffect()`​：

‍

```js
import { watchPostEffect } from 'vue'

watchPostEffect(() => {
  /* 在 Vue 更新后执行 */
})
```

## 手动停止侦听器

要手动停止一个侦听器，请调用 `watch`​ 或 `watchEffect`​ 返回的函数：

‍

```js
const unwatch = watchEffect(() => {})

// ...当该侦听器不再需要时
unwatch()
```

‍

‍

---

‍

```js
        // 1. 监视单个ref类型的数据
        watch(
            num1,
            (newVal, oldVal) => {
                console.log("数据发生改变", newVal, oldVal);
            },
            { immediate: true }
        );

        // 2. 监视多个ref数据, 放进数组内
        watch(
            [num1, num2],
            (newValArr, oldValArr) => {
                console.log("数据发生改变", newValArr, oldValArr);
            },
            { immediate: true }
        );

        // 3. 监视reactive对象内全部数据
        // 注意: 无法获取oldVal, 强制开启了深度监视
        watch(person, (newVal, oldVal) => {
            console.log("person发生改变", newVal, oldVal);
        });

        // 4. 监视reactive对象内某个属性, 将该属性写入函数内! 注意: 此时可以获取oldVal
        watch(
            () => person.name,
            (newVal, oldVal) => {
                console.log("person发生改变", newVal, oldVal);
            }
        );

        // 5.监视reactive对象内某些属性, 将包含该属性的函数放入一个数组内, 注意: 此时可以获取oldVal
        watch([() => person.name, () => person.age], (newVal, oldVal) => {
            console.log("person发生改变", newVal, oldVal);
        });
```

‍
