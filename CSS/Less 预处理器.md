# Less 预处理器

# 什么是less

* less是一个CSS预处理器, less文件后缀为.less
* 扩充了css语言, 是css具有一定逻辑性, 计算能力
* 注意:浏览器不识别Less代码, 目前阶段, 网页要引入对应的css文件.

# 注释

单行注释: //  
多行注释:/* */  
单行注释只能存在于less文件中

# 计算

* 加 减 乘 直接书写表达式
* 除 需要用小括号包裹, 或者使用./

```html
.box{
    width: 123*3 px;
    // height: 123./3 px;
    height: (123/3) px;
}
```

# 嵌套生成后代选择器

作用: 快速生成后代选择器  
语法: 直接在父选择器内书写子选择器

注意: &代表当前选择器, 一般用于hover等伪类选择器

```html
less语法:
.father{
    background-color: #fff;
    .son{
        height: 100px;
        &:hover{
            background-color: #ccc;
        }
    }
}


生成的css

.father {
  background-color: #fff;
}
.father .son {
  height: 100px;
}
.father .son:hover {
  background-color: #ccc;
}

```

# 变量

定义: @变量名: 数值;  
调用: @变量名

```html
less语法:

@color :red;


.box1{
    background-color: @color;
}

.box2{
    background-color: @color;
}
.box3{
    background-color: @color;
}

css代码

.box1 {
  background-color: red;
}
.box2 {
  background-color: red;
}
.box3 {
  background-color: red;
}

```

# 导入

语法:

> @import: "文件路径";

注意: 如果导入的是less文件, 那么文件后缀名可以省略

# 混合

定义一个类后, 在别处调用即可将该类的所有属性导入

```html
.bordered {
  border-top: dotted 1px black;
  border-bottom: solid 2px black;
}

#menu a {
  color: #111;
  .bordered();
}

.post a {
  color: red;
  .bordered();
}
```

# 转义

```html
@min768: (min-width: 768px);
.element {
  @media @min768 {
    font-size: 1.2rem;
  }
}
```

# 控制easy less导出路径

setting.json添加:

```html
    "less.compile": {
      
        "out": "../css/"

    },
```

单独设置:

在less文件第一行书写

> `//out: 文件路径/文件名`

# easy less 禁止导出

一般用于base/common.less等公共文件

在第一行加入:

> `//out: false`
