---
title: readonly &amp; shallowReadonly
date: 2022-11-04T13:57:52Z
lastmod: 2022-11-04T14:16:16Z
---

# readonly & shallowReadonly

```js
        let person = reactive({
            name: "tim",
            age: 18,
            job: {
                j1: {
                    money: 20,
                },
            },
        });

        person = readonly(person);
        person = shallowReadonly(person);
```

作用: `readonly`​可以让一个响应式数据变为只读的, `shallowReadonly`​为浅只读

应用: 不希望数据被修改时

‍
