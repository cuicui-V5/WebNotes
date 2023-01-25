---
title: Proxy 代理
date: 2022-11-02T14:13:42Z
lastmod: 2022-11-02T14:17:36Z
---

# Proxy 代理

使用代理可以实现对对象属性的修改或访问的响应式, 实现自定义操作, 使用defineProperty也可以部分实现, 但是无法做到监测对对象属性的新增或删除的监视数据监视的原理[^1]

语法: `const p = new window.Proxy(源对象, {配置对象})`​

配置对象可以包含: 

* get: 读取时触发
* set: 修改或新增属性时触发
* deleteProperty: 删除属性时触发

```js
	    const person = {
                name: "tim",
                age: 18,
                sex: "男",
            };
            console.log(person);
            const p = new window.Proxy(person, {
                get(target, propName) {
                    console.log("读取了" + propName);
                    return target[propName];
                },
                set(target, propName, val) {
                    console.log("修改或新增了" + propName);
                    target[propName] = val;
                    return target[propName];
                },
                deleteProperty(target, propName) {
                    console.log("删除了" + propName);
                    return delete target[propName];
                },
            });
```

‍

[^1]: # 数据监视的原理

    Vue会监视data中所有层次的数据

    # 监测对象中的数据

    通过setter实现监视, 且要在new Vue时就传入要监视的数据

    * 对象中后追加的属性, Vue默认不做响应式处理
    * 如果需要给后添加的属性做响应式, 使用如下api

      * `Vue.set(targey, propertyName/index,value)`
      * `vm.$.set(target,propertyName/index, value)`

    # 监测数组中的数据

    Vue通过包装方法实现, 本质上就是

    * 通过原生对应的方法对数组进行更新
    * 重新解析模板, 更新资源

    在Vue中修改数组中的某个元素一定要用数组的方法, 不能直接修改下标修改

    * `push(), pop(), shift(), unshift(), splice(), sort(), reverse() ​`
    * `Vue.set()`, 或`​ vm.$set()`

    ‍

    # 注意: 

    ==Vue.set() 和 vm.$set() 不能给vm或vm的根数据对象(vm._data)添加属性!==

    ‍

    # 简易的实现数据监视

    ```js
    const data = {
        name: "tim",
        age: 18,
    };
    const obs = new Observer(data);
    //实现监测数据
    /**
     *
     * @param {object} obj
     */
    function Observer(obj) {
        const keys = Object.keys(obj);
        keys.forEach(k => {
            Object.defineProperty(this, k, {
                get() {
                    return obj[k];
                },
                set(val) {
                    console.log(k, "被修改了");
                    obj[k] = val;
                },
            });
        });
    }
    ```
