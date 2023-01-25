---
title: computed
date: 2022-11-03T11:05:50Z
lastmod: 2022-11-03T11:09:13Z
---

# computed

在 Vue3 中计算属性需要先引用后在使用,

在 `setup ​`​ 中, 调用 `computed`​ 函数, 传入一个函数或者一个对象来使用计算属性

如果只需要读取数据, 那么直接传入一个函数即可, 函数返回值就为计算属性的值

如果还需要修改数据, 那么就需要传入一个对象, 对象内使用 `get ​`​和 `set ​`​来分别设置读取和修改的函数

‍

```js
import { reactive, computed } from "vue";
```

```js
        // 计算属性简写形式, 只需要读取不需要修改
        person.fullName = computed(() => {
            return person.firstName + "-" + person.lastName;
        });

        // 计算属性对象形式
        person.fullName = computed({
            get() {
                return person.firstName + "-" + person.lastName;
            },
            set(val) {
                const nameArr = val.split("-");
                person.firstName = nameArr[0];
                person.lastName = nameArr[1];
            },
        });
```
