# fs文件系统模块

fs 模块是 Node.js 官方提供的， 用来操作文件的模块， 它提供了一系列的方法和属性， 用来满足用户对文件的操作需求。

例如：

* `fs.readFile()` 方法 ，用来读取文件的内容
* `fs.writeFile()` 方法， 用来向指定的文件写入内容

```js
const fs = require("fs")
```

‍

# 读取指定文件中的内容

## fs.readFile()语法格式

使用 `fs.readFile()` 方法， 可以读取指定文件的内容， 语法格式如下：

```js
fs.readFile(path[,options],callback(err,res))
```

参数：

* `path` : 字符串， 文件路径
* `option ​`: 可选， 表示以什么编码格式读取文件 例如 `“utf8”`
* `callback`: 文件读取完成后， 执行回调

  * 回调函数的参数

    * `err ​` 失败结果
    * `res ​` 成功的结果

‍

注意：

* 如果读取成功， 那么 `err` 结果为 `null`
* 如果读取失败， `err` 为错误对象， res 为 `undefined`

# 向指定文件中写入内容

## fs.writeFile()的语法格式

```js
fs.writeFile(file,data[,option],callback(err))
```

参数：

* `file`: 文件路径
* `data`： 要写入的内容
* `option`： 文件编码， 默认 utf8
* `callback`： 写入完成后的回调函数

  * `err ​`：错误对象

注意：

* 如果写入成功， 那么 err 的值为 null
* 如果写入成功， err 则为错误对象
* 如果文件不存在， 那么会创建他
* ==writeFile 只能用来创建文件, 不能创建路径==
* 新写入的内容会覆盖旧写入的内容

‍

# 路径动态拼接问题

代码在运行的时候, ==会以执行 Node 命令时所处的目录==, 动态拼接出操作文件的完整路径

在使用 fs 模块操作文件时, 提供绝对路径, 不要使用相对文件路径

## 解决方法: __dirname

利用 Node 的全局变量,`__dirname` 来获取文件所处路径

```powershell
__dirname+"./1.txt"
```
