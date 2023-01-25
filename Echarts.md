---
title: Echarts
date: 2022-11-29T22:19:25Z
lastmod: 2022-11-29T22:21:36Z
---

# Echarts

# 基本使用

## 导入

```ts
    import * as echarts from "echarts";
```

## 初始化

```ts
    const myEcharts = echarts.init(ec.value);
```

## 设置参数

```ts
 myEcharts.setOption({...})
```

注意: 

* 必须给echarts容器设置宽高, 才能显示

```ts
<template>
    <div class="about">
        <!-- echarts的容器, 必须设置宽高, 否则不显示 -->
        <div
            class="echarts"
            ref="ec"
        ></div>
    </div>
</template>
<script lang="ts" setup>
    // 引入echarts
    import * as echarts from "echarts";
    import { ref, onMounted } from "vue";
    const ec = ref<HTMLElement | null>(null);
    onMounted(() => {
        console.log("111");
        console.log(ec.value);

        if (ec.value != null) {
            const myEcharts = echarts.init(ec.value);
            myEcharts.setOption({
                // 设置参数
                title: {
                    text: "ECharts 入门示例",
                },
                tooltip: {},
                legend: {
                    data: ["销量"],
                },
                xAxis: {
                    data: [
                        "衬衫",
                        "羊毛衫",
                        "雪纺衫",
                        "裤子",
                        "高跟鞋",
                        "袜子",
                    ],
                },
                yAxis: {},
                series: [
                    {
                        name: "销量",
                        type: "bar",
                        data: [5, 20, 36, 10, 10, 20],
                    },
                ],
            });
        }
    });
</script>

<style lang="scss">
    @media (min-width: 1024px) {
        .about {
            min-height: 100vh;
            display: flex;
            align-items: center;
        }
    }
    .echarts {
        width: 400px;
        height: 600px;
    }
</style>
```
