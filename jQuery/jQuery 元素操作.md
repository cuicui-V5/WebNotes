# jQuery 元素操作

遍历 创建 添加 删除元素

# 遍历元素

jQuery隐式迭代是对同一类元素做了相同的操作, 如果相对同一类元素做不同操作, 需要用到遍历

## jQuery元素.each() 方法

`$("div").each(function(index.domEle){xxx;})`

* `each`方法遍历匹配的每一个元素, 主要用`DOM`处理, each每一个
* 里面的回调函数有两个参数: `index`是每个元素的索引号, ==domEle是每个DOM元素对象, 不是jQuery对象==
* 要想使用jQuery方法, 需要把这个DOM元素转换为jQuery对象, `$(domEle)`

# $.each()方法

`$.each(object,function(index.element{xxx;}))`

* `$.each()`方法可用于遍历任何对象, 主要用于数据处理, 比如数组, 对象
* 里面的函数有两个参数, `index`是每个元素的索引号., `element`遍历内容

# 创建元素

`$("<li><li>")`;

动态的创建了一个`li`标签

# 添加元素

## 内部添加

`element.append(元素);`

添加到匹配元素内部的最后面

`element.prepend(元素);`

添加到匹配元素内部的最前面

内部添加元素, 生成之后, 他们是父子关系

## 外部添加

`element.after("内容")`

把内容放到目标元素后面

`element.before("内容")`

把内容放到目标元素前面

外部添加元素, 生成之后, 他们是兄弟关系

‍

# 删除元素

`element.remove();​`

删除匹配的元素本身

`element.empty();`

删除匹配元素里面的子节点

`element.html("");`

清空节点里面的内容

‍
