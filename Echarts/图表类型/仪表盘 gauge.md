---
title: 仪表盘 gauge
date: 2022-12-03T17:48:44Z
lastmod: 2022-12-03T18:04:26Z
---

# 仪表盘 gauge

# data格式

```js
                data: [
                    {
                        value: 900,
                    },
                ],
```

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
                // 仪表盘
                type: "gauge",
                max: 1000,
		// 进度条
                progress: {
                    show: true,
                },
                data: [
                    {
                        value: 900,
                    },
                ],
            },
        };
```

‍

‍
