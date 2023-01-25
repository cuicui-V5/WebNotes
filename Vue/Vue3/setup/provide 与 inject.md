---
title: provide 与 inject
date: 2022-11-05T15:04:33Z
lastmod: 2022-12-08T17:13:13Z
---

# provide 与 inject

![Snipaste_2022-11-05_15-04-26](assets/Snipaste_2022-11-05_15-04-26-20221105150451-tk3chjj.png)​

一种祖孙间通信方式

在祖先组件中使用`provide`​提供数据, 在后代组件中使用`inject`​使用数据

```js
// 祖先组件
provide("person", person);

// 后代组件
let person = inject("person");

console.log(person);
```

# 依赖注入

这两个方法一般用于在app中注入依赖, 方便子组件使用

# 如何搭配typeScript使用依赖注入时标注类型

```ts
import { provide, inject } from 'vue'
import type { InjectionKey } from 'vue'

const key = Symbol() as InjectionKey<string>

provide(key, 'foo') // 若提供的是非字符串值会导致错误

const foo = inject(key) // foo 的类型：string | undefined
```

### provide

新建一个存储key的ts文件

```ts
import type { InjectionKey } from "vue";
import type { Axios } from "axios";

export const axiosKey = Symbol() as InjectionKey<Axios>;
```

在app中provide

```ts
    import { provide } from "vue";
    import axios from "axios";
    import { axiosKey } from "./key";

    provide(axiosKey, axios);
```

### inject 

```ts
import { axiosKey } from '@/key';
import { inject } from 'vue';
const axios = inject(axiosKey)
```

此时axios的类型即为 `Axios`​

‍

## 特殊情况, 搭配echarts使用

### key.ts

```ts
import type { InjectionKey } from "vue";
import type Echarts from "echarts";

export const echartsKey = Symbol() as InjectionKey<typeof Echarts>;
```

### provide

```ts
    import { provide } from "vue";
    import * as echarts from "echarts";
    import { echartsKey} from "./key";

    provide(echartsKey, echarts);
    provide(axiosKey, axios);
```

### inject

```ts
    import type { EChartsOption } from "echarts";
    import type Echarts from "echarts";

    import { inject, onMounted } from "vue";
    import { echartsKey} from "../key";

    const chart = inject<typeof Echarts>(echartsKey);

    onMounted(() => {
        let container = document.querySelector(".abc") as HTMLElement;
        console.log(container);

        const myChart = chart?.init(container, "dark");
        const option: EChartsOption = {
            title: {
                text: "test",
            },
            xAxis: {},
            yAxis: {},
            series: {
                data: [1, 2, 3, 4],
                type: "bar",
            },
        };
        myChart?.setOption(option);
    });
```
