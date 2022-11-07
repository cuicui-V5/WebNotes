# reactive对比ref

# 从定义数据角度对比

* ​`ref` ​用来定义: 基本类型数据
* ​`reactive` ​用来定义: 引用类型(对象, 数组)

注意: `ref` ​也可以用来定义对象类型数据, 它内部会自动使用 `reactive` ​转为代理对象

‍

# 从原理角度对比

* ​`ref` ​通过 `O`​`bject.defineProperty()`​ 的 `get` ​和 `set` ​实现响应式(数据劫持)
* ​`reactive` ​通过使用 `Proxy ​` ​来实现响应式, 并通过 `Reflect` ​操作源对象内部的数据

‍

# 从使用角度对比

* ​`ref` ​定义的数据: 操作数据需要 .`value`​, 在模板中不需要.`value`​
* ​`reactive` ​定义的数据, 操作数据不需要.`value`​

‍
