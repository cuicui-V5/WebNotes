---
title: &lt;script setup&gt;写法
date: 2022-11-05T16:13:53Z
lastmod: 2022-12-28T00:35:30Z
---

# <script setup>写法

```js
<script setup>
import { ref, reactive, provide } from "vue";
import AppSon from "./components/AppSon.vue";

let msg = ref("hello iam app");
let person = reactive({
    name: "tim",
    age: 17,
});

</script>
```

‍

注意:

* 使用此写法, 不再需要`setup()`​函数, 也不再需要`return {}`​
* 顶层的变量和引入的组件可以直接在模板中使用
* 使用`defineProps`​和`defineEmits`​来导入`props`​和`emits`​

‍

# 使用`defineProps`​

父组件传来的数据, 可以使用`defineProps`​接收

```js
//父组件
       <AppSon :p="person" @hello="handler"></AppSon>

// 子组件
	const props = defineProps(["p","q"]);
	注意: 这里不能直接使用结构赋值, 需要使用toRefs
 	const {p,q} = toRefs(props)
在模板中可以直接使用p这个变量

```

​`defineProps`​使用TS类型标注

```ts
const props = defineProps<{
  foo: string
  bar?: number
}>()

const emit = defineEmits<{
  (e: 'change', id: number): void
  (e: 'update', value: string): void
}>()
```

# 使用`defineEmits`​

```js
let emit = defineEmits(["hello"]);

function chufa() {
    emit("hello", 666);
}
```
