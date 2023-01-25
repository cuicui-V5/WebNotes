---
title: Vue router 基本使用
date: 2022-10-26T10:06:09Z
lastmod: 2022-10-26T17:25:51Z
---

# Vue router 基本使用

## 安装

首先需要安装 vue-router

```js
npm i vue-router@3 
```

注意: 

* vue-router@3 搭配vue2, vue3适配4以后版本

# 引入并使用

在 `main.js`​ 引入并使用`vue-router`​

```js
import VueRouter from "vue-router";

Vue.use(VueRouter);
```

# 新建路由规则

新建 `Router/index.js`​, 在配置对象中传入 `routes`​数组来指定路由规则, 用 `path`​指定路径, `component`​指定匹配规则对应的路径

```js
import MyAbout from "../components/MyAbout.vue";
import MyHome from "../components/MyHome.vue";

import VueRouter from "vue-router";
export default new VueRouter({
    routes: [
        {
            path: "/MyAbout",
            component: MyAbout,
        },
        {
            path: "/MyHome",
            component: MyHome,
        },
    ],
});
```

# 配置跳转

使用 `<router-link>`​标签来设置路由链接, 用 `go`​ 属性指向路径, `active-class`​ 指定激活时的类名

```html
<router-link class="list-group-item" active-class="active" to="MyAbout">
About
</router-link>
<router-link class="list-group-item" active-class="active" to="MyHome">
Home
</router-link>
```

在页面中, 使用`<router-view>`​标签来指定显示路由组件的区域

‍

注意:

* 路由组件通常存放在 `pages`​文件夹, 一般组件通常存放在 `components`​文件夹
* 切换时, 路由组件默认是被销毁的, 需要的时候再挂载
* 每个组件都有自己的 `$route`​属性, 里面存储着自己的路由信息
* 整个应用只有一个 router, 可以通过组件的 `$router`​属性获取到
