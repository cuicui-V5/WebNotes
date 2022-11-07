# mixin 混入

功能: 可以把多个组件共同的配置提取成一个混入对象

# 使用

## 定义混入

新建 `mixin.js`​

```js
export const mixin = {
    mounted() {
        console.log(this);
    },
};

```

## 使用混入

### 全局混入

全局混入会在每个组件中都进行混入

在 `main.js`​ 中, 使用 `Vue.mixin(mixin);`​ 进行混入

```js
import App from "./App.vue";
import Vue from "vue";

import { mixin } from "./components/mixin.js";

Vue.mixin(mixin);

new Vue({
    el: ".root",
    render: h => h(App),
});

```

### 局部混入

在组件中, 使用`mixins: [mixin]`​ 配置项进行混入

```js
<template>
    <div>
        <h1 id="school">学校名称是 {{ name }}</h1>
    </div>
</template>

<script>
import { mixin } from "./mixin.js";
export default {

    name: "MySchool",
    data() {
        return {
            name: "xx小学",
        };
    },
    mixins: [mixin]
};
</script>

<style>
#school {
    color: violet;

    font-size: 20px;
}
</style>
```
