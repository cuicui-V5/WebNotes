# jQuery 样式操作

# 操作css方法

jQuery可以使用css方法来修改简单元素样式, 也可以操作类, 修改多个样式

# 

* 参数只写属性名, 则是返回属性值

  `&(this).css("color");`

* 参数是 `属性名, 属性值` 用逗号分隔, 属性必须加引号, 值如果是数字就不用加单位和引号

  `$(this).css("color","red");`

* 参数可以是对象形式, 方便设置多组属性, 属性名和属性值用冒号隔开, 属性值可以不用加引号

  `$(this),css({color:"white",bacogroundColor:"pink​"})​`

‍

# 设置类样式方法

作用等同于以前的calssList , 可以操作类样式, 注意参数不要加点

1. 添加类

    `$("div").addClass("current");`
2. 移除类

    `$("div").removeClass("current");`
3. 切换类

    `$("div").toggleClass("current");`

‍
