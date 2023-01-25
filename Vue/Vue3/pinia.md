---
title: pinia
date: 2022-11-16T09:18:39Z
lastmod: 2022-11-16T09:36:07Z
---

# pinia

pinia 是一个类似 vuex 的状态管理库, 支持组合式api

# 定义store

使用 `defineStore`​ 来定义一个`store`​

第一个参数为store id, 第二个参数为配置对象

​`defineStore()`​ 的第二个参数可接受两类值：Setup 函数或 Option 对象。

```js
import { defineStore } from 'pinia'

// 你可以对 `defineStore()` 的返回值进行任意命名，但最好使用 store 的名字，同时以 `use` 开头且以 `Store` 结尾。(比如 `useUserStore`，`useCartStore`，`useProductStore`)
// 第一个参数是你的应用中 Store 的唯一 ID。
export const useStore = defineStore('main', {
  // 其他配置...
})
```

## 选项式api写法

与 Vue 的选项式 API 类似，我们也可以传入一个带有 `state`​、`actions`​ 与 `getters`​ 属性的 Option 对象

你可以认为 `state`​ 是 store 的数据 (`data`​)，`getters`​ 是 store 的计算属性 (`computed`​)，而 `actions`​ 则是方法 (`methods`​)。

```js
export const useCounterStore = defineStore('counter', {
  state: () => ({ count: 0 }),
  getters: {
    double: (state) => state.count * 2,
  },
  actions: {
    increment() {
      this.count++
    },
  },
})
```

## 选项式api写法

```js
export const useCounterStore = defineStore('counter', () => {
  const count = ref(0)
  function increment() {
    count.value++
  }

  return { count, increment }
})
```

在 *Setup Store* 中：

* ​`ref()`​ 就是 `state`​ 属性
* ​`computed()`​ 就是 `getters`​
* ​`function()`​ 就是 `actions`​

# 使用 Store

在sfc中使用store

```js
import { useCounterStore } from '@/stores/counter'

export default {
  setup() {
    const store = useCounterStore()

    return {
      // 为了能在模板中使用它，你可以返回整个 Store 实例。
      store,
    }
  },
}
```

## 提取属性

使用	`storeToRefs()`​来提取属性

```js
import { storeToRefs } from 'pinia'

export default defineComponent({
  setup() {
    const store = useCounterStore()
    // `name` and `doubleCount` 都是响应式 refs
    // 这也将为由插件添加的属性创建 refs
    // 同时会跳过任何 action 或非响应式(非 ref/响应式)属性
    const { name, doubleCount } = storeToRefs(store)
    // 名为 increment 的 action 可以直接提取
    const { increment } = store

    return {
      name,
      doubleCount,
      increment,
    }
  },
})
```
