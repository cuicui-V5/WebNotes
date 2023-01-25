---
title: 饼状图 pie
date: 2022-12-01T15:10:05Z
lastmod: 2022-12-03T14:42:20Z
---

# 饼状图 pie

饼状图不需要有`xAxis`​​和`yAxis`​​

# data格式

```html
                data: [
                    { value: 10, name: "吃饭" },
                    { value: 50, name: "睡觉" },
                    { value: 30, name: "打飞机" },
                    { value: 20, name: "玩电脑" },
                    { value: 21, name: "喝水" },
                ],
```

# 设置环形图

设置`radius`​属性, 传入一个数组, 数组内第一个参数为内圈半径, 第二个参数为外圈半径

# 设置玫瑰图

​`roseType`​: "`area`​",

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
            series: {
                name: "test",
                type: "pie",
                data: [
                    { value: 10, name: "吃饭" },
                    { value: 50, name: "睡觉" },
                    { value: 30, name: "打飞机" },
                    { value: 20, name: "玩电脑" },
                    { value: 21, name: "喝水" },
                ],

                // 设置内外半径
                // 第一个参数表示内部空白区域占容器宽度的比例, 第一个参数必须小于第二个参数
		// 第二个参数表示外圈占容器总宽度的比例,
                radius: ["20%", "70%"],
                // 是否设置成玫瑰图
                roseType: "area",
                itemStyle: {
                    borderRadius: "10",
                },
                // 是否显示文本标签
                label: {
                    show: true, // 是否显示文本标签
                    position: "inside",
                },
            },
```
