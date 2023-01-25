---
title: vuex 模块化 namespace
date: 2022-10-23T13:57:20Z
lastmod: 2022-10-25T10:50:10Z
---

# vuex 模块化 namespace

修改 `store/index.js`​

```js
const increaseSpace = {
    namespaced: true, //必须使用此项来开启 命名空间
    actions: {
        increaseOdd(context, val) {
            if (context.state.num % 2 !== 0) {
                context.commit("IncreaseOdd", val);
            }
        },
    },
    mutations: {
        increase(state, value) {
            console.log("mutation被执行了");
            console.log(state, value);
            state.num += value;
        },
    },
    state: {
        num: 2,
    },
    getters: {
        bigNum(state) {
            return state.num * 10;
        },
    },
};
const PersonSpace = {
    namespaced: true,
    actions: {
        addPerson(context) {
            context.state.person.unshift({
                name: "new P",
                age: 14,
                sex: "male",
            });
        },
    },
    state: {
        person: [ ],
    },
};

// 创建并暴露store
export default new Vuex.Store({
    modules: {
        increaseSpace,
        PersonSpace,
    },
});

```

在对象中定义 `actions`​, `mutations`​, `state`​, `getters`​, 并且使用 `namespaced: true`​ 开启命名空间

在 vuex 的配置对象中, 使用 `modules: { )`​ 注册

‍

开启命名空间后, 在组件中读取 `state ​`​数据

```js
	通过mapState 
       ...mapState("increaseSpace", ["num", "name", "age", "address", "person"]),

	直接读取
	this.$store.state.increaseSpace.num;
```

在组件中读取 `getters`​ 数据

```js
	通过mapGetters
        ...mapGetters("increaseSpace", ["bigNum"]),

	直接读取
	this.$store.getters["increaseSpace/bigNum"];
```

在组件中读取 `dispatch`

```js
	直接调用dispatch
	this.$store.dispatch("PersonSpace/addPerson");

	通过mapAction
        ...mapActions("increaseSpace", ["increaseOdd", "increaseDelay"]),
```

在组件中调用 `commit`​

```js
	直接调用commit
	this.$store.commit("PersonSpace/addPerson");

	借助 mapMutation
        ...mapMutations("increaseSpace", ["increase", "decrease"]),

```

‍

注意: 

* 必须要配置`namespaced: true`​ 开启命名空间
