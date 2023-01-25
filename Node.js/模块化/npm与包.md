---
title: npm与包
date: 2022-09-01T09:34:31Z
lastmod: 2022-09-13T15:37:13Z
---

# npm与包

## 包

### 什么是包

Node.js 的第三方模块又叫做包

### 包的来源

包由第三方个人或第三方团队开发

Node.js 中的包都是免费开源的, 不需要付费

### 为什么要使用包

由于 Node.js 的内置模块仅提供了一些底层的 API, 导致在基于内置模块进行项目开发时, 效率很低

包是基于内置模块封装出来的, 提供了更高级, 更方便地 API, 很大的提高了开发效率

‍

### 从哪下载包

[npmjs.com](https://www.npmjs.com/)

‍

## npm 包管理工具

### 如何下载包

使用 npm(node Packge Manager)来安装包

### npm 的使用方法

1. 使用 npm 包管理工具, 在项目中安装包

   1. `npm install 包的完整名称`
2. 使用 `require` 导入包
3. 使用包

### 在项目中安装包

‍

```js
npm install packgeName

简化形式
npm i packgeName

全局安装 使用-g命令
npm i nrm -g 

安装指定版本的包
npm i moment@2.22

一次性安装所有缺失的包(在packge.json里面记录的)
npm install 或
npm i
```

#### 切换包服务器

```powershell
查看当前的下包服务器
npm config get registry

切换下包服务器
npm config set registry=服务器地址
npm config set registry https://registry.npm.taobao.org

```

还可以使用 nrm 工具来切换包服务器

```powershell
nmp i nrm -g
查看所有可用的镜像源
nrm ls
切换
nrm user taobao
```

### 在项目中卸载包

```js
npm uninstall 包名
```

卸载包后, 会自动将该包从 `packge.json` 从移除

### 包管理配置文件

初次装包后, 在项目文件夹下多了一个叫做 `node_module` 的文件夹和 `packge-lock.json` 的配置文件

‍

其中:

* `node_module` 文件夹存放了所有已安装到项目中的包, `require()` 导入第三方包后, 就从这个目录中查找
* `packge-lock.json` 配置文件用来记录 `node_module.json` 目录下的每一个包的下载信息, 例如包的名字, 版本号, 下载地址等

在项目根目录中, 必须提供一个叫做 `packge.json` 的包配置文件, 用来记录与项目有关的一些信息

* 项目的名称, 版本号, 描述等
* 项目中都用到了哪些包
* 哪些包只有在开发期间会用到
* 哪些包在开发和部署都需要用到

#### 快速创建 packge.json

`npm` 包管理工具提供了一个快捷命令, 可以在执行命令时所处的目录中, 快速创建 `packge.json` 这个包管理配置文件

```js
在执行命令所处的目录中, 快速创建packge.json配置文件
npm init -y
```

注意:

* 上述命令只能在英文的目录下运行, 所以 项目文件夹的名称一定要使用英文
* 运行 `npm install` 命令安装包的时候, `npm` 包管理工具会自动把包的名称和版本号, 记录到 `packge.json` 中

‍

#### `dependencies` 节点

`dependencies` 节点用来记录使用 `npm install` 安装了哪些包

‍

#### `devDependencies` 节点

如果某些包只在项目开发阶段会用到,在项目上线之后不会用到, 建议把这些包记录到 `devDependencies` 节点中

如果在开发和项目上线后都需要用到, 那么建议记录到 `dependencies` 节点

```js
安装到devDependencies中
npm i 包名 -D

完整写法
npm install 包名 --save-dev
```

‍

### 包的语义化版本规范

包的版本号以点分十进制形式定义, 例如 1.22.33

其中每一位数字包含的含义如下:

* 第一位数字: 大版本
* 第二位数字: 功能版本
* 第三位数字: bug 修复版本

版本号提升原则:

* 只要前面的版本号提升了, 那么后面的版本号归零

### 包的分类

#### 项目包

那些被安装到项目的 `node_modules` 目录中的包, 都是项目包

项目包又分为两类,分别是

* 开发依赖包 (被记录到 `devDependencies` 节点中的包, 只有在开发期间被用到)
* 核心依赖包 (被记录到 `dependencies` 节点的包, 在开发和部署中都会用到的包)

‍

#### 全局包

在执行 `npm install ​` 命令时, 如果提供了 `-g` 参数, 则会把包安装为全局包

全局包会被安装到 `C:\Users\用户名\AppData\Roming\npm\node_modules`

```powershell
全局安装包
npm i 包名 -g

全局卸载包
npm uninstall 包名 -g
```

* 只有工具性质的包, 才有全局安装的必要性, 因为它们提供了好用的终端命令
* 判断是否需要全局安装, 建议参考官方文档

‍

### 规范的包结构

一个规范的包, 他的组成结构, 必须符合以下三点

* 包必须以单独的目录存在
* 包的根目录下必须包含 packge.json 这个包管理配置文件
* packge.json 中必须包含以下三个属性

  * name: 包的名字
  * version: 版本号
  * main: 包的入口

### 开发自己的包

‍

步骤:

1. 新建项目文件夹
2. 新建如下三个文件

   1. packge.json 包配置管理文件
   2. index.js 包的入口文件
   3. README.md 包的说明文档

‍

#### packge.json 模板

<br />

```powershell
{
    "name": "my_package", 包的名称, 唯一不重复
    "version": "1.0.0", 版本号
    "description": "", 对包的简短描述 
    "main": "index.js", 指定包的润口文件
    "keywords": [], 关键词
    "license": "ISC" 开源许可协议
}
```

#### 将不同功能进行模块化拆分

1. 将不同的功能的模块拆分到 `scr` 目录下不同的 `js` 文件内
2. 在 `index.js` 中, 导入这两个模块, 得到需要向外共享的方法
3. 在 `index.js` 中, 使用 `module.exports` 将对应方法共享出去

‍

### 发布包

在包的根目录打开终端, 执行以下命令即可发布包到npm上, (注意 包名不可重复)

```powershell
npm publish
```

### 删除已经发布的包

使用以下命令从npm删除已经发布的包

```powershell
npm unpublish 包名 --force
```

注意: 

* unpublish 只能删除72小时以内发布的包
* 通过unpublished删除的包, 24小时内不能重复发布
* 要慎重发包
