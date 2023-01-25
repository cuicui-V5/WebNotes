---
title: ref 模板引用
date: 2022-11-15T17:31:39Z
lastmod: 2022-11-16T09:09:13Z
---

# ref 模板引用

‍

在Vue3.0 ==组合式api==中, 需要声明一个同名的`ref`​

```js
<script setup>
import { ref, onMounted } from 'vue'

// 声明一个 ref 来存放该元素的引用
// 必须和模板里的 ref 同名
const input = ref(null)

onMounted(() => {
  input.value.focus()
})
</script>

<template>
  <input ref="input" />
</template>
```
