# Bootstrap

## 目录

*   [使用步骤](#使用步骤)

*   [Bootstrap文档](#bootstrap文档)

*   [Bootstrap栅格系统](#bootstrap栅格系统)

    *   [container类名](#container类名)

    *   [container-fluid](#container-fluid)

    *   [col和row](#col和row)

    *   [如何让子级紧贴父级无边距](#如何让子级紧贴父级无边距)

*   [Bootstrap全局CSS样式](#bootstrap全局css样式)

*   [Bootstrap组件](#bootstrap组件)

*   [Bootstrap插件](#bootstrap插件)

# 使用步骤

1.  引入

    ![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1650352595359-3aee30ba-c240-424d-be81-7188b05f7c3e.png#clientId=u62e7ff82-ca73-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=122\&id=uca5855b5\&margin=\[object Object]\&name=image.png\&originHeight=122\&originWidth=1057\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=57906\&status=done\&style=none\&taskId=u70f6c84d-68ca-47a6-92eb-642c964c07c\&title=\&width=1057>)

2.  调用类

    *   container: 响应式布局版心类

# Bootstrap文档

# Bootstrap栅格系统

*   栅格化是指将整个屏幕的宽度分成了若等分

*   Bootstrap 3 默认将网页分成 12 等分

|            |           |          |           |           |
| ---------- | --------- | -------- | --------- | --------- |
|            | 超小屏幕      | 小屏幕      | 中等屏幕      | 大屏幕       |
| 相应断点       | < 768px   | >=768px  | >=992px   | >=1200px  |
| 别名         | xs        | sm       | md        | lg        |
| 容器宽度       | 100%      | 750px    | 970px     | 1170px    |
| 类前缀 \*代表列数 | col-xs-\* | col-sm-^ | col-md-\* | col-lg-\* |
| 列数         | 12        | 12       | 12        | 12        |
| 列间距        | 30px      | 30px     | 30px      | 30px      |

## container类名

*   .container 类用于固定宽度并支持响应式布局的容器。

*   container 所有使用此类名的盒子都被指定宽度并且居中., 容器宽度见上表

*   **container自带间距15px**

## container-fluid

*   .container-fluid 类用于 100% 宽度，占据全部视口（viewport）的容器。

*   所有应用该类名的盒子, 宽度均为100%

## col和row

*   Bootstrap分别使用col和row定义行和列

*   **row自带间距-15px**

## 如何让子级紧贴父级无边距

给子级再加一层父级, 类名为row

```html
<div class="box container">
  <div class="row">
    <div class="son col-lg-2 col-md-6">1</div>
    <div class="son col-lg-2 col-md-6">2</div>
    <div class="son col-lg-2 col-md-6">3</div>
    <div class="son col-lg-2 col-md-6">4</div>
    <div class="son col-lg-2 col-md-6">5</div>
    <div class="son col-lg-2 col-md-6">6</div>
    <div class="son col-lg-2 col-md-6">7</div>
    <div class="son col-lg-2 col-md-6">8</div>
    <div class="son col-lg-2 col-md-6">9</div>
    <div class="son col-lg-2 col-md-6">10</div>
  </div>
    </div>
```

# Bootstrap全局CSS样式

# Bootstrap组件

# Bootstrap插件

注意:

*   由于Bootstrap插件依赖于jQuery 所以引入js时, 先引入jQuery , 再引入 Bootstrap
