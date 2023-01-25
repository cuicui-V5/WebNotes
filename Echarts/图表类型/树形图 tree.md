---
title: 树形图 tree
date: 2022-12-03T21:49:29Z
lastmod: 2022-12-03T21:51:25Z
---

# 树形图 tree

# 设置树的方向

​`orient: "TB",`​

取值可以为 `LR, RL, TB, BT ​`​等

‍

# 设置子树的展开关闭

data内设置`collapsed`​, `false`​为展开, `true`​为关闭

‍

‍

```js
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
                type: "tree",
                // 布局方向
                orient: "TB",
                data: [
                    {
                        name: "root",
                        children: [
                            {
                                name: "1",
                                children: [
                                    {
                                        name: "3",
                                        collapsed: false,
                                        children: [
                                            {
                                                name: "AgglomerativeCluster",
                                                value: 3938,
                                            },
                                            {
                                                name: "CommunityStructure",
                                                value: 3812,
                                            },
                                            {
                                                name: "HierarchicalCluster",
                                                value: 6714,
                                            },
                                            {
                                                name: "MergeEdge",
                                                value: 743,
                                            },
                                        ],
                                    },
                                    {
                                        name: "4",
                                    },
                                ],
                            },
                            { name: "2" },
                        ],
                    },
                ],
            },
        };
```
