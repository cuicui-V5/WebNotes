---
title: 折线图 line
date: 2022-12-01T16:27:32Z
lastmod: 2022-12-01T17:54:41Z
---

# 折线图 line

与柱状图基本类似

# 设置折线平滑

​`smooth`​: `true`​, // 开启平滑过渡

‍

# 选中高亮效果

如果设置了多个系列, 可以使用选中高亮效果

                    `emphasis`​: {  
                        `focus`​: "`series`​",  
                    },

```ts
 const option: ECOption = {
            title: {
                text: "标题",
                subtext: "副标题",
                left: "left",
                top: "left",
            },
            tooltip: {},
            legend: {
                orient: "vertical",
            },
            xAxis: {
                data: [1, 2, 3, 4, 5],
            },
            yAxis: {},
            series: [
                {
                    name: "test",
                    type: "line", // 折线图
                    smooth: true, // 开启平滑过渡
                    areaStyle: {
                        color: "skyblue",
                    },
                    emphasis: {
                        //选中高亮效果
                        focus: "series",
                    },
                    data: [
                        { value: 10, name: "吃饭" },
                        { value: 31, name: "睡觉" },
                        { value: 30, name: "打飞机" },
                        { value: 20, name: "玩电脑" },
                        { value: 21, name: "喝水" },
                    ],
                },
                {
                    name: "test",
                    type: "line", // 折线图
                    smooth: true, // 开启平滑过渡
                    areaStyle: {},
                    emphasis: {
                        //选中高亮效果
                        focus: "series",
                    },
                    data: [
                        { value: 5, name: "吃饭" },
                        { value: 20, name: "睡觉" },
                        { value: 10, name: "打飞机" },
                        { value: 15, name: "玩电脑" },
                        { value: 21, name: "喝水" },
                    ],
                },
            ],
```

‍
