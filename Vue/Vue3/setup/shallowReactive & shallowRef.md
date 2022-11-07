# shallowReactive & shallowRef

​`shallowReactive`​: 只处理对象最外层的响应式 (浅响应式)

​`shallowRef`​: 只处理基本数据类型的响应式, 不进行对象的响应式处理

应用:

* 如果有一个对象数据, 结构比较深, 但只有最外层属性变化, 那么就用 `shallowReactive`​
* 如果有一个对象数据, 后续不会修改对象中的属性, 而是生成新的对象来替换 , 那么使用 `shallowRef`​

‍
