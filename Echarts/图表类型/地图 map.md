---
title: 地图 map
date: 2022-12-04T14:35:23Z
lastmod: 2022-12-04T14:45:36Z
---

# 地图 map

ts使用需要引入

```js
        MapChart,
        GeoComponent,
        MapSeriesOption
        GeoComponentOption
```

# 获取地图数据

[https://datav.aliyun.com/portal/school/atlas/area_selector](https://datav.aliyun.com/portal/school/atlas/area_selector)

```js
        let { data: mapData } = await axios.get(
            "https://geo.datav.aliyun.com/areas_v3/bound/100000_full.json",
        );
```

# 注册地图

```js
        echarts.registerMap("chinaMap", mapData);
```

# 配置文件

```js
        const option: ECOption = {
            geo: {
                type: "map",
                map: "chinaMap",
                // 可进行拖动缩放
                roam: true,
                // 初始缩放
                zoom: 1.5,
                // 初始中心
                center: [105.4, 33.99],
                label: {
                    show: true,
                    position: "inside",
                },
                itemStyle: {
                    color: "pink",
                },
            },
        };
```

# 地图上叠加散点图

增加一个`series`​配置项即可, 注意`coordinateSystem`​要设置为 `geo`​, 表示按照地理坐标来绘制散点图

```js
        const option: ECOption = {
            tooltip: {},
            geo: {
                type: "map",
                map: "chinaMap",
                // 可进行拖动缩放
                roam: true,
                // 初始缩放
                zoom: 1.5,
                // 初始中心
                center: [105.4, 33.99],
                label: {
                    show: false,
                    position: "inside",
                },
                itemStyle: {
                    color: "pink",
                },
            },
            series: {
                type: "scatter",
                // 按照什么来绘制散点图
                coordinateSystem: "geo",
                data: [
                    {
                        name: "北京",
                        value: [108, 34],
                        symbolSize: 50,
                    },
                ],
            },
        };
```
