# path路径模块

`path` 模块是 Node.js 官方提供的, 用来处理路径的模块, 他提供了一系列的方法和属性, 用来满足用户对路径的处理需求

例如:

* `path.join()` 方法 将多个路径片段拼接成一个完整的路径字符串
* `path.basenamne()` 方法,用来从路径字符串中, 将文件名解析出来

导入:

```powershell
const path = require("path")
```

‍

# 路径拼接

## path.join() 的语法格式

利用 `path.join()` 方法, 可以把多个路径片段拼接为完整的路径字符串, 语法格式如下:

```powershell
path.join([...paths])
```

参数:

`...paths`: 路径片段的序列

返回值:

`string ​` 字符串

示例:

```powershell
const pathStr = path.join(__dirname,"./files/1.txt")
```

‍

# 获取路径中的文件名

## path.basename()的语法格式

使用 `path.basename() ​` 方法, 可以获取路径的最后一部分, 通常使用这个方法, 获取路径中的文件名, 语法格式如下:

```powershell
path.basename(path[,ext])
```

参数:

* `path` 表示一个路径的字符串
* `ext ​` 可选, 表示文件扩展名

返回值:

路径的最后一部分的字符串

‍

注意:

* `basename` 的第二个参数, 表示从结果中去掉后缀名, 例如本来结果是 `index.html,` 第二个参数为 `.html`, 那么输出就为 `index`, 如果第二个参数为 `html`,那么结果就是 `index. ​` 所以第二个参数只是简单的从后移除匹配项目

‍

‍

# 获取路径中的文件扩展名

## path.extname() 的语法格式

使用 `path.extname()` 方法, 可以获取路径中的扩展名部分, 语法格式如下

```powershell
path.extname(path)
```

参数:

* `path` 路径字符串

返回值:

* 返回得到的扩展名字符串
