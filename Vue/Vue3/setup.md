---
title: setup
date: 2022-11-01T20:38:46Z
lastmod: 2022-12-27T00:18:04Z
---

# setup

# 拉开序幕的 setup

```js
<script>
import { ref } from 'vue'

export default {
  setup() {
    const count = ref(0)

    // 返回值会暴露给模板和其他的选项式 API 钩子
    return {
      count
    }
  },

  mounted() {
    console.log(this.count) // 0
  }
}
</script>

<template>
  <button @click="count++">{{ count }}</button>
</template>
```

* Vue3 的一个新的配置项, 值为一个==函数==
* ​`setup ​`​​​是所有 Composition API (组合式 API) 表演的舞台
* 组件中所用到的数据 方法等, 均要配置在 `setup ​`​​​中
* ​`setup ​`​​​函数的两个返回值:

  * 对象: 对象中的属性, 方法, 在模板中均可使用
  * 若返回一个渲染函数, 则可自定义渲染内容

注意:

* 尽量不要与 Vue2 的配置混用

  * Vue2 的配置 (`data`​​, `methods`​​, `computed`​​..)可以访问到 `setup ​`​​中的属性, 方法
  * 但是 Vue3 的 `setup ​`​​不能访问 Vue2 的配置
  * 如果有重名, `setup ​`​​优先
* ​`setup ​`​​不能是一个 `async ​`​​函数, 因为返回值不再是 `return ​`​​的对象, 而是 `promise`​​

‍

‍

# setup的两个注意点

* ​`setup`​的执行时机

  * 在`beforeCreate`​之前执行一次, this是undefined
* ​`setup`​的参数

  * ​`props`​: 值为对象, 包含:组件外部传递过来, 且组件内部用`props`​声明接收了的属性
  * ​`context`​: 上下文对象

    * ​`attrs`​: 值为对象, 包含: 组件外部传递过来, 但没有在`props`​配置中声明的属性
    * ​`slots`​: 收到的插槽内容, 相当于`this.$slots`​
    * ​`emit`​: 触发自定义事件的函数, 相当于`this.$emit`​

‍
