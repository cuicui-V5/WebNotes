# Flex布局

## 目录

*   [作用](#作用)

*   [设置方式](#设置方式)

*   [组成部分](#组成部分)

*   [特点](#特点)

*   [主轴对齐方式: justfy-content:](#主轴对齐方式-justfy-content)

*   [侧轴对齐方式align-items / align-self](#侧轴对齐方式align-items--align-self)

*   [多行弹性盒子侧轴对齐方式align-content](#多行弹性盒子侧轴对齐方式align-content)

    *   [align-items和 align-content的区别](#align-items和-align-content的区别)

*   [弹性盒子尺寸](#弹性盒子尺寸)

*   [弹性伸缩比](#弹性伸缩比)

*   [修改主轴方向 flex-direction](#修改主轴方向-flex-direction)

*   [弹性盒子自动换行 flex-wrap](#弹性盒子自动换行-flex-wrap)

## 作用

*   基于Flex精确灵活控制块级盒子的布局方式,避免浮动脱标

*   flex布局非常适合结构化布局

## 设置方式

*   父元素添加 display: flex; 子元素可以自动地挤压或拉伸

## 组成部分

*   弹性容器

*   弹性盒子

*   主轴

*   侧轴 / 交叉轴

## 特点

*   设置display: flex; 后, 弹性盒子默认沿主轴排列

## 主轴对齐方式: justfy-content:

| 属性值        | 含义                  |
| ---------- | ------------------- |
| flex-start | 默认值, 从起点开始依次排列, 左对齐 |
|            |                     |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649762435608-d24f253e-7954-4258-b78a-ca9d6fc9f140.png#clientId=uee3bd651-eb1f-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=256\&id=uce822953\&margin=\[object Object]\&name=image.png\&originHeight=256\&originWidth=885\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=12349\&status=done\&style=none\&taskId=u91d1f0d2-f0e5-428d-b09f-a09dda902cc\&title=\&width=885>)

| flex-end | 从终点开始依次排列, 右对齐 |
| -------- | -------------- |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649762451959-592a7778-6c34-442c-9d25-edc022ac423e.png#clientId=uee3bd651-eb1f-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=268\&id=u5c3642a9\&margin=\[object Object]\&name=image.png\&originHeight=268\&originWidth=891\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=12984\&status=done\&style=none\&taskId=u8928d38b-b949-4436-95fb-650f1818358\&title=\&width=891>)

| center | 居中, 无间距 |
| ------ | ------- |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649762350251-e4b92b5a-0501-482e-9d2c-8491f7af4b9e.png#clientId=uee3bd651-eb1f-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=264\&id=uf9d40b0e\&margin=\[object Object]\&name=image.png\&originHeight=264\&originWidth=885\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=13414\&status=done\&style=none\&taskId=u2907f688-2db0-4938-9c25-52c330b143b\&title=\&width=885>)

| space-around | 居中均匀分布. 弹性盒子左右的边距相同, 效果是边框空间小, 盒子之间空间大 |
| ------------ | -------------------------------------- |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649762322111-8241dc93-226d-4b63-8717-723529501898.png#clientId=uee3bd651-eb1f-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=271\&id=ueceba0d1\&margin=\[object Object]\&name=image.png\&originHeight=271\&originWidth=885\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=15336\&status=done\&style=none\&taskId=u175e7ff8-797d-489b-b0f6-0e8bc14932c\&title=\&width=885>)

| space-between | 居中均匀分布, 弹性盒子与边框无间距, 弹性盒子之间间距相同 |
| ------------- | ------------------------------ |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649762278830-38ac7949-d361-4916-8e50-48e193655d71.png#clientId=uee3bd651-eb1f-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=256\&id=ud66504d6\&margin=\[object Object]\&name=image.png\&originHeight=256\&originWidth=887\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=14211\&status=done\&style=none\&taskId=u549c862e-15e4-49fd-b5ab-81bbe1a4fc6\&title=\&width=887>)

| space-evenly | 真\` 居中均匀分布, 所有间距完全相同 |
| ------------ | -------------------- |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649762302246-6acab796-3f70-4466-ad94-fd72d9dc4dd8.png#clientId=uee3bd651-eb1f-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=261\&id=u15cd2992\&margin=\[object Object]\&name=image.png\&originHeight=261\&originWidth=878\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=14879\&status=done\&style=none\&taskId=udad6ddd5-3b0b-4be8-9e67-65ccb007d15\&title=\&width=878>)

## 侧轴对齐方式align-items / align-self

*   align-items :添加到弹性容器, 设置所有弹性盒子的样式 (给父级)

*   align-self: 控制某个弹性盒子在侧轴的对齐方式 (给子级)

|            |                           |
| ---------- | ------------------------- |
| 属性值        | 含义                        |
| flex-start | 上对齐                       |
| flex-end   | 下对齐                       |
| center     | 居中对齐                      |
| stretch    | 默认值, 当弹性盒子没有设置默认高度时, 拉伸高度 |

## 多行弹性盒子侧轴对齐方式align-content

### align-items和 align-content的区别

相同点:&#x20;

*   都用来设置对齐行为

不同点:

*   align-items 设置对象是行内成员

*   align-content设置对象是所有行, 只有在多行弹性盒子中才会生效

属性：align-content
属性值：

| 属性值        | 含义             |
| ---------- | -------------- |
| flex-start | 从起点开始依次排列, 上对齐 |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649857484002-09190b93-8cbb-4273-ae69-a017722ef611.png#clientId=u116400c8-cf90-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=680\&id=u2f9345c2\&margin=\[object Object]\&name=image.png\&originHeight=680\&originWidth=681\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=26122\&status=done\&style=none\&taskId=u0a8881cd-43a1-4137-b086-1e3596ee58f\&title=\&width=681>)

| flex-end | 从终点开始依次排列, 下对齐 |
| -------- | -------------- |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649857559820-4d996c98-2ac1-4a4e-82e6-7ccc5a25e5c4.png#clientId=u116400c8-cf90-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=671\&id=uafc8e899\&margin=\[object Object]\&name=image.png\&originHeight=671\&originWidth=670\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=21382\&status=done\&style=none\&taskId=ub68be754-e3a3-4520-bdc6-bae22afe8eb\&title=\&width=670>)

| center | 居中, 无间距 |
| ------ | ------- |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649857576378-11aab7cb-655d-4b95-b540-91a3a3864220.png#clientId=u116400c8-cf90-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=676\&id=uf3197b99\&margin=\[object Object]\&name=image.png\&originHeight=676\&originWidth=677\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=22923\&status=done\&style=none\&taskId=uec2c6d6a-d331-45e7-a0ef-9e36aac2c77\&title=\&width=677>)

| space-around | 居中均匀分布. 弹性盒子上下的间距相同, 效果是边框空间小, 盒子之间空间大 |
| ------------ | -------------------------------------- |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649857593961-98a485a3-0654-417b-97b3-e5a470a45c61.png#clientId=u116400c8-cf90-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=681\&id=u02b746c8\&margin=\[object Object]\&name=image.png\&originHeight=681\&originWidth=683\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=26222\&status=done\&style=none\&taskId=u3004d656-af2e-4ecf-b18b-3ebe1acb71f\&title=\&width=683>)

| space-between | 居中均匀分布, 弹性盒子与边框无间距, 弹性盒子之间间距相同 |
| ------------- | ------------------------------ |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649857608586-b57f8fe2-0f31-474b-b771-5e6c45d0a2d3.png#clientId=u116400c8-cf90-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=678\&id=u147007c8\&margin=\[object Object]\&name=image.png\&originHeight=678\&originWidth=678\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=22544\&status=done\&style=none\&taskId=ue24ed01c-288a-48a1-a789-4cf83403535\&title=\&width=678>)

| space-evenly | 真\` 垂直居中均匀分布, 所有间距完全相同 |
| ------------ | ---------------------- |

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649857635815-5e0887a6-53b8-4d3a-97d3-55a92d5554ef.png#clientId=u116400c8-cf90-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=684\&id=uf904ee4d\&margin=\[object Object]\&name=image.png\&originHeight=684\&originWidth=679\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=22986\&status=done\&style=none\&taskId=u627675d9-1e73-44a9-bb44-c851ce55857\&title=\&width=679>)

## 弹性盒子尺寸

*   如果设置了宽高, 那么就为宽高

*   如果没有设置高度, 那么默认为拉伸高度, 除非align设置为非stretch

*   如果没有设置宽度, 那么宽度默认为内容宽度

## 弹性伸缩比

属性:flex
属性值: 数字倍数
含义:
弹性盒子相对于盒子剩余部分的比例

```html
.box div:nth-child(1){
   flex: 1;
}
.box div:nth-child(2){
    flex: 2;
}
.box div:nth-child(3){
    flex: 3;
}
.box div:nth-child(4){
    flex: 4;
}
```

\*\*给四个元素分别设置为1,2,3,4 \*\*
**那么四个元素的宽度比例为1:2:3:4**

![](<https://cdn.nlark.com/yuque/0/2022/png/25905096/1649768911816-1c11d33e-5b20-415a-b6f9-99f2a82879ad.png#clientId=uee3bd651-eb1f-4\&crop=0\&crop=0\&crop=1\&crop=1\&from=paste\&height=331\&id=uc95e0354\&margin=\[object Object]\&name=image.png\&originHeight=422\&originWidth=895\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=21396\&status=done\&style=none\&taskId=u2a529ebb-c179-4a53-8cdd-808d5dcdb64\&title=\&width=703>)

## 修改主轴方向 flex-direction

| 属性值            | 含义       |
| -------------- | -------- |
| row            | 默认值，从左往右 |
| column         | 从上往下     |
| row-reverse    | 从右往左     |
| column-reverse | 从下往上     |

## 弹性盒子自动换行 flex-wrap

属性： flex-wrap
属性值：

*   wrap：换行

*   nowrap： 默认，不换行
