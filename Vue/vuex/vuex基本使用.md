---
title: vuex基本使用
date: 2022-10-22T16:42:50Z
lastmod: 2022-11-16T09:25:09Z
---

# vuex基本使用

创建文件 `src/store/index.js`​

```js
// 引入Vue核心库
import Vue from "vue";
// 引入vuex
import Vuex from "vuex";

// 应用vuex插件, 注意. 不要放到main.js中, 会造成引入顺序问题
Vue.use(Vuex);

// 准备actions;,mutations,state对象
const actions = {};
const mutations = {};
const state = {};

// 创建并暴露store
export default new Vuex.Store({
    actions,
    mutations,
    state,
});
```

2. 在`main.js`​中, `new Vue ​`​时传入`store`​配置项

```js
import Vue from "vue";
import App from "./App.vue";
import store from "./store";

Vue.config.productionTip = false;

new Vue({
    store,
    render: h => h(App),
}).$mount("#app");
```

# 基本使用

在 `store/index.js`​ 中,  配置 `action`​ , `mutation`​, 和 `state`​

```js
// 引入Vue核心库
import Vue from "vue";
// 引入vuex
import Vuex from "vuex";

// 应用vuex插件, 注意. 不要放到main.js中, 会造成引入顺序问题
Vue.use(Vuex);

// 准备actions;,mutations,state对象
const actions = {
    increaseOdd(context, val) {
        if (context.state.num % 2 !== 0) {
            context.commit("IncreaseOdd", val);
        }
    },
};
const mutations = {
    increase(state, value) {
        console.log("mutation被执行了");
        state.num += value;
    },

};
const state = {
    num: 2,
};

// 创建并暴露store
export default new Vuex.Store({
    actions,
    mutations,
    state,
});
```

组件中使用vuex中的数据

## 读取数据

在组件中读取vuex中的数据: `$store.state.num`

## 修改数据

修改数据可以调用 `commit ​`​或 `dispatch`​, 前者直接调用 `mutation`​ 中的方法, 后者调用 `action`​中的方法

```js
	increase() {
            this.$store.commit("increase", this.step);
        },

        increaseOdd() {
            this.$store.dispatch("increaseOdd", this.step);
        },
```

‍

# getters的使用

当`state`​中的数据需要加工后在使用时, 可以使用`getters`​加工, 类似 `computed`​

在 `store/index/js ​`​中添加 `getters ​`​配置项

```js
const getters = {
    bigNum(state) {
        return state.num * 10;
    },
};

// 创建并暴露store
export default new Vuex.Store({
    actions,
    mutations,
    state,
    getters,
});
```

## 读取getters中的数据

`$store.getters.bigNum`

‍

# 四个map方法

通过使用`map`​方法, 可以方便的使用vuex中的方法和数据, 不再需要  $store.

map系列方法有

* ​`mapState`​
* ​`mapGetters`​
* ​`mapActions`​
* ​`mapMutations`​

```js
	import { mapState, mapGetters, mapMutations, mapActions } from "vuex";

   	 computed: {
	        // mapState的对象写法
	        // ...mapState({
	        //     name: "name",
	        //     age: "age",
	        //     address: "address",
	        // }),
	        // mapState的数组写法
	        ...mapState(["num", "name", "age", "address"]),
	        ...mapGetters(["bigNum"]),
	    },
	    methods: {
	        ...mapActions(["increaseOdd", "increaseDelay"]),
	        ...mapMutations(["increase", "decrease"]),
	    },
```

注意: 

* ​`mapActions`​​和`mapMutations`​​如果需要传递参数, 需要在调用的时候加上参数:

  `<button @click="increase(step)">+</button>`​​

‍
