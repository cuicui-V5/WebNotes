---
title: jQuery基础
date: 2022-08-04T09:16:22Z
lastmod: 2022-08-04T11:38:51Z
---

# jQuery基础

# 

# jQuery的基本使用

## jQuery的入口函数

jQuery的入口函数有两种, 推荐第一种

```js
            //jquery的入口函数

            $(function () {
                //此处是DOM加载的入口
                $("div").hide();
            });

            $(document).ready(function () {
                //此处是DOM加载的入口
            });
```

* 等着ODOM解构渲染完毕即可执行代码, 不必等到所有外部资源加载完成
* 相当于原生js中的DOMContentLoaded

# jQuery中的顶级对象 $

`$` 是 jQuery的别称, 在代码中可以使用`jQuery`代替 `$` , 但是为了方便, 一般直接使用`$`

`$`是  jQuery的顶级对象, 相当于原生 JavaScript 中的 `window` , 把元素利用 `$` 包装成 jQuery 对象, 就可以调用 jQuery 的方法

‍

# jQuery对象和DOM对象

* 用原生JS获取的对象就是DOM对象
* jQuery方法获取的元素就是jQuery对象
* jQuery对象本质是: 利用$对DOM对象包装后产生的对象(为数组形式存储)
* ==jQuery对==​==象只能用jQuery方法, DOM元素只能使用原生JavaScript方法==

## jQuery对象和DOM对象互相转换

DOM对象和jQuery对象是可以互相转换的

‍

DOM对象转换为jQuery对象

`$(DOM对象)`

jQuery对象转换为DOM对象

方法1: `$('div')[0];`

方法2: `$('div').get(0);`

```js
            //DOM元素获取方式
            let d = document.querySelector("div");

            //jq获取方式
            $("div").hide();

            //dom对象转换为jq对象
            $(d).hide(); //直接将dom元素放入$中即可

            // 第一种 jq对象转换为dom对象 的方法
            $("div")[0].style.backgroundColor = "red"; //因为是伪数组, 所以可以用[0] 获取dom元素
            // 第二种 jq对象转换为dom对象 的方法
            $("div").get(0).style.backgroundColor = "pink";
```

‍
