---
title: 背景background系列属性
date: 2022-07-17T20:43:41Z
lastmod: 2023-01-02T15:45:35Z
---

# 背景background系列属性

# 背景

## 背景颜色

属性名 : background-color (bgc)

属性值: 颜色取值: 关键字, rgb表示法, rgba表示法, 十六进制表示法

注意:

* 背景颜色默认为透明: rgba(0,0,0,0), transparent
* 背景颜色不会影响盒子大小, 而且还能看清合资的大小和位置,一般在布局中会首先设置背景颜色

属性名: background-image (bgi)

属性值: background-image: url('图片路径');

注意:

* 背景图片中url中可以省略引号
* 背景图片默认是在水平和垂直方向平铺的
* 背景图片仅仅是指给盒子起到装饰效果, 类似于背景颜色, 不能撑起盒子的

## 背景平铺

属性名: background-repeat (bgr) 属性值:

|取值|效果|
| -----------| ------------------|
|repeat|水平和垂直都平铺|
|no-repeat|不平铺|
|repeat-x|沿水平平铺|
|repeat-y|沿着垂直方向平铺|

## 背景位置

属性名: background-position (bgp)

属性值: background-position: 水平方向位置 垂直方向位置 ;

取值:

* 方位名词 水平: left center right 垂直 top center bottom
* 数字+px 坐标系, 图片左上角的坐标

注意: 方位名词和坐标取值可以混合使用, 第一个取值表示水平, 第二个名词表示垂直.

## 背景图片大小

作用：设置背景图片的大小 属性：background-size：宽度 高度 取值：

|取值|含义|
| ---------| ----------------------------------------------------------|
|数字+px|宽度高度|
|百分比|相对于当前盒子宽高的百分比|
|contain|将背景图片等比例放大，但不会超过盒子尺寸，有可能留下空白|
|cover|将图片等比例放大，直到将盒子盖住，这样不会留下空白|

## 背景相关属性连写

属性名: background (bg)

属性值: 单个属性值的合写, 取值之间使用空格隔开

书写顺序: 推荐 background : color image repeat position/size 也可以自由顺序

注意:

* 可以按照需求省略
* 在pc端, 如果盒子大小和背景图片大小一致, 那么可以直接写 background : url();
* 如果需要设置单独的样式和连写
* 要么把单独的样式写在连写的下面
* 要么把单独的样式写在连写的里面.

## img和background区别

效果: 在网页中显示一张图

方法一: 直接写上img标签, img标签不设置宽高直接会默认以图片原尺寸显示

方法二: div标签+background 样式 需要设置div的宽高, 因为 background 只是样式, 不能撑起 div 标签

## 如何让背景图完美显示

如何让一张大图完美的成为背景图

## 渐变背景linear-gradient

语法：background-image：linear-gradient（ 颜色1， 颜色2， 颜色3 ）；

透明：transparent

‍

# 控制背景图和背景颜色如何混合`background-blend-mode`

​`background-blend-mode`​ CSS 属性定义该元素的背景图片，以及背景色如何混合。
