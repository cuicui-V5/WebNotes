# ref函数

作用: 定义一个响应式的数据

语法: 

​`const xxx = ref(initVal)`​

​`ref`​可以创建一个包含响应式数据的==引用对象==​,​ (reference对象, 简称ref对象)

操作数据: `xxx.value`

模板读取数据: 不需要value, 直接写即可

注意: 

* 接受的数据可以是基本类型, 也可以是对象类型

  * 基本类型的数据, 内部响应式依然是`Object.defineProperty()`​的`get`​与`set`​实现的
  * 对象类型的数据. 内部"求助"了Vue3的新函数: `reactive ​`​函数

‍

‍

‍
