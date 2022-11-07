# 元素偏移量offset系列属性

## 目录

*   [offset概述](#offset概述)

*   [offset与style区别](#offset与style区别)

# offset概述

offset翻译过来就是偏移量, 我们使用offset系列相关属性可以动态的得到该元素的位置(偏移), 大小等

&#x20;

*   可以获取距离**带有定位**的父元素的位置

*   获取元素本身的大小

*   注意 : 返回值不带单位

*   注意: 非直接父元素也可以

| 属性             | 作用                                        |
| -------------- | ----------------------------------------- |
| e.offsetParent | 返回带有定位的父元素, 如果都没有那么返回body                 |
| e.offsetTop    | 返回元素距离定位父元素顶部的偏移量                         |
| e.offsetLeft   | 返回元素距离定位父元素左边的偏移量                         |
| e.offsetWidth  | 返回自身的宽度(包括border padding  和 content) 不带单位 |
| e.offsetHeight | 返回自身的高度(包括border padding  和 content) 不带单位 |

注意:

*   此处的父元素可以是非直接的父元素

*   `offsetWidth`和`offsetHeight`获取的是元素的实际大小, 不包括`margin`, 包括`padding`和`border`(设置`box-sizing:border-box`后, width/height是多少就是多少)

*   这些属性为 **只读属性** , 不可更改

# offset与style区别

offset

*   offset可以获得任意样式表中的值

*   offset获得的值没有单位

*   默认情况下获取的宽高包括padding和border

*   offset属性只读

*   想获取元素大小位置, 用offset更合适

style

*   style只能得到行内样式表中的值

*   style获得的是由单位的字符串

*   style获取的是实际的样式值

*   style属性可读写

*   想更改样式, 用style
