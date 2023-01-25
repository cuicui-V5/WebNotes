---
title: Vue3中 v-model封装自定义组件实现数据双向绑定
date: 2023-01-14T15:48:30Z
lastmod: 2023-01-17T16:03:34Z
---

# Vue3中 v-model封装自定义组件实现数据双向绑定

v-model传进来的数据为`modelValue`​, 要手动触发的事件为`update:modelValue`​

父组件

```ts
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <test v-model="msg"></test>
  </div>
</template>
```

子组件

```ts
<template>
  <div>
    请输入
    <input
      type="text"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>

<script>
export default {
  props: ["modelValue"],
};
</script>
```
