---
title: Vue核心
date: 2022-09-15T10:23:41Z
lastmod: 2022-11-01T14:49:34Z
---

# Vue核心

```js
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
        <script src="./js/vue.js"></script>
    </head>
    <body>
        <div class="root">
            <h1>hello {{name}}</h1>
        </div>
        <script>
            Vue.config.productionTip = false;
            new Vue({
                el: ".root",
                data: {
                    name: "tim",
                },
            });
        </script>
    </body>
</html>
```

* 要想让Vue工作， 就必须创建一个Vue实例， 且要传入一个配置对象
* root容器里面的代码依然符合html规范， 只不过混入了一些特殊的Vue语法
* root容器里的代码称为 ==Vue模板==
* Vue实例和容器是一一对应的
* 真是开发中只有一个Vue实例, 并且会配合着组件一起使用
* `{{}}` 里面的为js表达式, 可以读取到`data`里面所有的数据
* 一旦`data`中的数据发生改变, 那么模板中的数据会自动改变

# 模板语法

html中包含了一些js语法代码, 语法分为两种: 

* 插值语法 `{{}}`
* 指令 `v-`开头

## 插值语法

用于解析标签体内容

语法:  `{{js表达式}}` 表达式可以直接读取data中的内容

## 指令语法

用于解析标签(标签属性, 标签体内容, 绑定事件)

语法`v-bind:src="url"` 

注意 : Vue中有很多指令, 形式都是`v-xxx`

‍

# 数据绑定

Vue中有两种数据绑定的方式: 

* 单向绑定(`v-bind`), 数据只能从`data`流向页面
* 双向绑定(`v-model`): 数据不仅能从`data`流向页面, 还能从页面流向`data`

注意: 

* 双向绑定一般都运用在表单类元素上
* ==`v-model:value`==​==​ 可以简写为==​==`v-model,`==​==​ 因为==​==`v-model`==​==默认收集的就是value值==

‍

# el和data的两种写法

## el的两种写法

* ​`new Vue`​时候配置`el`​属性
* 先创建Vue实例, 然后通过`vm.$mount(".root") ​`​进行挂载

‍

## data的两种写法

* 对象式
* 函数式

注意: 函数式不能写箭头函数

‍
