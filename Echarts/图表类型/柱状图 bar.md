---
title: 柱状图 bar
date: 2022-12-01T14:49:42Z
lastmod: 2022-12-03T14:41:59Z
---

# 柱状图 bar

# data格式

​`data: [12, 42, 54, 34, 54],`​

# 设置方向

只需要设置`xAxis`​的`type`​为`value`​, `yAxis`​的`type`​为`category`​即可

# 设置最大值最小值平均值指示器

在`series`​中设置`markPoint`​, `markLine`​即可

```ts
        const option: ECOption = {
            title: {
                text: "标题",
                subtext: "副标题",
                // left: "center",
            },
            tooltip: {
                // 提示框触发方式: item 只有在图形上才会触发, axis在范围内都会触发
                trigger: "axis",
                // 坐标轴指示器 line 线, shadow 阴影, cross , 十字线准星效果
                axisPointer: {
                    type: "cross",
                },
                // 是否显示提示框
                showContent: true,
                // 样式
                backgroundColor: "pink",
                textStyle: {
                    fontSize: "20",
                },
                // 内容格式化
                // formatter: (p) => {
                //     return "value=" + p;
                // },
            },
            // 图例
            legend: {
                // 是否显示图例
                show: true,
                // 图标形状
                icon: "circle",
                // 设置位置
                top: "1%",
            },
            xAxis: {
                type: "value",
            },
            yAxis: {
                type: "category", // 类型. 类目轴
                data: ["1", "2", "3", "4", "5"],
            },
            series: {
                name: "test",
                type: "bar",
                data: [12, 42, 54, 34, 54],
                markPoint: {
                    data: [
                        {
                            type: "max",
                            name: "最大值",
                        },
                        {
                            type: "min",
                            name: "最xiao值",
                        },
                    ],
                },
                markLine: {
                    data: [
                        {
                            type: "average",
                            name: "平均",
                        },
                    ],
                },
            },
        };
```

‍
