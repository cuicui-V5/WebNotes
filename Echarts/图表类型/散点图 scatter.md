---
title: 散点图 scatter
date: 2022-12-01T19:56:33Z
lastmod: 2022-12-03T14:43:50Z
---

# 散点图 scatter

# data格式

```html
                data: [
                    [1, 3],
                    [2, 5],
                    [5, 3],
                    [6, 5],
                    [5, 2],
                    [4, 4],
                    [6, 4],
                    [2, 4],
                    [6, 6],
                ],
```

与柱状图和折线图相似, 都需要横轴和纵轴

​`series`​中的`data`​需要设置为二维数组

* ​`symbolSize`​: 设置点的大小

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
            xAxis: {},
            yAxis: {},
            series: {
                name: "test",
                type: "scatter",
                data: [
                    [1, 3],
                    [2, 5],
                    [5, 3],
                    [6, 5],
                    [5, 2],
                    [4, 4],
                    [6, 4],
                    [2, 4],
                    [6, 6],
                ],
                symbolSize: 50, // 散点图图形大小
                // 散点图图形样式
                color: {
                    // 线性渐变
                    type: "pattern",
                    x: 0,
                    x2: 1,
                    y: 1,
                    y2: 1,
                    colorStops: [
                        { offset: 0, color: "#fb7299" },
                        { offset: 1, color: "#0288d1" },
                    ],
                },
                emphasis: {
                    // focus: "self",
                    itemStyle: {
                        borderColor: "red",
                        borderWidth: 5,
                    },
                },
                // 是否显示文本标签
                label: {
                    show: true, // 是否显示文本标签
                    position: "inside",
                },
            },
        };
```

‍
