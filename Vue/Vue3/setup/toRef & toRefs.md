---
title: toRef &amp; toRefs
date: 2022-11-04T10:22:51Z
lastmod: 2022-11-04T10:28:08Z
---

# toRef & toRefs

*基于响应式对象上的一个属性，创建一个对应的 ref。这样创建的 ref 与其源属性保持同步：改变源属性的值将更新 ref 的值，反之亦然。*

作用: 创建一个`ref`​对象, 其`value`​值指向另一个对象的某个属性

语法: `const name = toRef(person,"name")`

应用: 需要将响应式对象中的某个属性单独提供给外部使用时

```js
        return {
            num1,
            num2,
            person,

            // toRef对单个属性实现引用
            name: toRef(person, "name"),
            age: toRef(person, "age"),
        };
```

## toRefs

批量创建多个ref对象组成的数组, 可以使用`...`​展开运算符使用

```js
        return {
            num1,
            num2,
            person,

            // toRef对单个属性实现引用
            ...toRefs(person),
        };
```
