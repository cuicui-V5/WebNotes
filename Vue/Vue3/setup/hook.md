---
title: hook
date: 2022-11-03T21:46:33Z
lastmod: 2022-11-04T09:22:22Z
---

# hook

​`hook` ​本质是一个函数, 把 `setup` ​函数中使用的 composition API 进行了封装

类似于 `mixin`​

优点: 复用代码, 让 `setup` ​中的逻辑更加清晰

‍

新建 `src/hook/usePoint.js`​

```js
import { reactive, onMounted } from "vue";
export default function () {
    let point = reactive({});

    onMounted(() => {
        window.addEventListener("click", givePos);
    });
    const givePos = function (e) {
        console.log(e.pageX, e.pageY);
        point.x = e.pageX;
        point.y = e.pageY;
    };
    return point;
}
```

在组件中使用 `hook`​

```js
<script>
import usePoint from "../hook/usePoint";
export default {
    name: "TestDemo",
    setup() {
        let point = usePoint();

        return { point };
    },
};
</script>
```
