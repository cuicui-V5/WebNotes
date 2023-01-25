---
title: 漏斗图 funnel
date: 2022-12-03T17:48:08Z
lastmod: 2022-12-03T17:48:41Z
---

# 漏斗图 funnel

# data格式

```js
                data: [
                    { value: 10, name: "吃饭" },
                    { value: 31, name: "睡觉" },
                    { value: 30, name: "打飞机" },
                    { value: 20, name: "玩电脑" },
                    { value: 21, name: "喝水" },
                ],
```

# 配置文件

```js
        const option: ECOption = {
            title: {
                text: "标题",
                subtext: "副标题",
                left: "left",
                top: "left",
            },
            tooltip: {},

            series: {
                name: "test",
                // 漏斗图
                type: "funnel",
                data: [
                    { value: 10, name: "吃饭" },
                    { value: 31, name: "睡觉" },
                    { value: 30, name: "打飞机" },
                    { value: 20, name: "玩电脑" },
                    { value: 21, name: "喝水" },
                ],
                // 排序方式
                sort: "ascending",
                emphasis: {
                    focus: "self",
                    label: {
                        fontSize: "30",
                    },
                },
            },
        };
```
