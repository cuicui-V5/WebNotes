---
title: app组件法
date: 2022-10-18T18:46:48Z
lastmod: 2022-10-18T18:46:55Z
---

# app组件法

# app组件法

在App组件中, 添加一个方法用于接收数据

```js
    methods: {
        addTodo(todoItemObj) {
            console.log(todoItemObj);
            this.todo.unshift(todoItemObj)
        },
    },
```

将该方法通过props方法传入子组件内

​`<TodoHeaderVue :addTodo="addTodo"></TodoHeaderVue>`​

然后子组件就可以使用该方法来提交数据
