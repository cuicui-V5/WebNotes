---
title: webpack
date: 2022-09-13T14:24:19Z
lastmod: 2022-09-14T16:28:08Z
---

# webpack

# 什么是 webpack

webpack 是前端项目工程化的具体解决方案

它提供了有好的前端模块化开发支持, 代码压缩混淆, 处理浏览器端 js 的兼容性, 性能优化等强大的功能

好处: 让程序员把工作的中心放到具体功能的实现上, 提高了前端开发效率, 和项目的可维护性

注意: 目前 Vue, React 等前端项目, 基本上都是基于 webpack 进行工程化开发的

‍

# 在项目中安装 webpack

```js
npm install webpack webpack-cli -D
```

# 在项目中使用 webpack

1. 在项目根目录中， 创建名为 `webpack.config.js` 的 webpack 配置文件， 并初始化如下的基本配置

   1. ```js
      module.exports = {
          mode: "development", //指定构建模式， 可选值有development, production
      };
      ```
2. 在 `packge.json` 的 `script ​` 节点下， 新增 `dev ​` 脚本

   1. ```js
          "scripts": {
              "dev": "webpack"
          },
      ```

      注意： `script` 节点下的脚本， 可以通过 `npm run ​` 运行
3. 在终端中运行 `npm run dev` 启动 `webpack` 对项目进行打包构建

# webpack.config.js 文件的作用

`webpack.config.js` 是 `webpack` 的配置文件， `webpack` 在真正开始打包构建之前， 会先读取这个配置文件， 从而基于给定的配置， 对项目进行打包

‍

注意： 由于 `webpack` 是基于 `node.js` 开发出来的打包工具， 因此在他的配置文件中， 支持使用 `node.js` 相关的语法和模块进行 `webpack` 的个性化配置

‍

# 自定义打包的入口与出口

默认的打包入口文件为 `scr/index.js`

默认的输出文件路径为 `dist/main.js`

‍

注意: 可以在 `webpack.config.js` 中通过 `entry` 和 `output` 节点修改打包的默认入口与出口

## 

```js
const path = require("path");

module.exports = {
    mode: "production", //指定构建模式， 可选值有development, production
    entry: path.join(__dirname, "./src/index.js"), //指定打包入口
    output: {
        path: path.join(__dirname, "./dist"), //输出文件的存放位置
        filename: "bundle.js", //输出文件的命名
    },
};
```

‍

# webpack 插件

## webpack-dev-server

每当修改了源代码, 自动进行打包和构建

### 安装

```js
npm i webpack-dev-server -D
```

### 使用

在 `packge.json` 中修改 `script` 脚本

```js
    "scripts": {
        "server": "webpack serve",
        "dev": "webpack"
    },
```

`webpack.config.js` 的 `devServer` 节点中, 可以指定 devServer 的参数

```js
    devServer: {
        open: true,
        port: 80,
        host: "127.0.0.1",
    },
```

注意: 修改配置文件后, 需要重启 `devServer`

## html-webpack-plugin

### 使用

```js
const HtmlWebpackPlugin = require("html-webpack-plugin");
const htmlWebpackPlugin = new HtmlWebpackPlugin({
    template: path.join(__dirname, "./src/index.html"),
    filename: "index.html",
});
module.exports = {
    plugins: [htmlWebpackPlugin],
};
```

注意:: `html-webpack-plugin` 可以自动引入 `webpack` 里面的静态资源

‍

# loader 加载器

在开发过程中, webpack 默认只能打包以 .js 的模块,  其他的文件 webpack 不能处理, 需要调用 loader 加载器才可以正常打包,

‍

loader 加载器的作用: 协助 webpack 打包处理特定的文件模块  比如:

* css-loader 处理.css 相关的文件
* less-loader 处理.less 相关的文件
* babel-loader 处理 webpack 无法处理的高级 js 语法

## Loader的使用

### 安装 loader

处理css

```js
npm i style-loader css-loader -D
```

处理less

```js
npm i less-loader less -D
```

处理文件url 图片转base64

```js
npm i url-loader file-loader -D
```

处理高级语法

webpack 只能打包一部分js的高级语法, 对于那些webpack无法处理的高级js语法, 需要借助于 babel-lodaer进行打包处理

```js
npm i babel-loader @babel/core @babel/plugin-proposal-decorators -D
```

### 使用 loader

在 `webpack.config.js` 的 `rule` 节点内, 添加 `loader` 规则

```js
    module: {
        rules: [
            {
                test: /\.css$/,
                use: ["style-loader", "css-loader"],
            },
            {
                test: /\.less$/,
                use: ["style-loader", "css-loader", "less-loader"],
            },
            {
                test: /\.jpg|png|gif$/,
                use: ["url-loader?limit=20000"],
            },
            {
                test: /\.js$/,
                use: ["babel-loader"],
                exclude: /node_modules/, //排除node_modules文件夹, 因为模块的代码已经被处理好了
            },
        ],
    },
```

其中, `test` 表示匹配的文件类型, `use` 表示使用的 `loader`

注意:

* `use` 数组中指定的 `loader` 顺序是固定的
* ==多个 loader 的调用顺序是从后向前调用==
* `loader`的参数可以使用查询字符串的形式, 也可以用`option`对象

```js
            {
                test: /\.jpg|png|gif$/,
                use: [
                    {
                        loader: "url-loader",
                        options: { limit: 2000, outputPath: "image" },
                    },
                ],
            },
```

‍

‍

### loader 的工作流程

1. `webpack ​`默认只能处理 .js 的文件, 处理不了其他类型的文件
2. 由于代码中包含了 `index.css` 这个文件, 因此 `webpack` 默认处理不了
3. 当 webpack 发现某个文件处理不了的时候, 就会查找配置文件下的 `module.rules` 数组中, 是否配置了对应的加载器
4. `webpack ​`把 `index.css` 先转交给最后一个 `loader ​`进行处理
5. 当这个 `loader ​`处理完成后, 会把处理的结果转交给下一个 `loader`
6. 当第一个 `loader ​`处理完成后, 发现没有下一个 `loader ​`了, 将最终处理的结果转交给 `webpack`
7. `webpack` 把 `loader ​`的处理结果, 合并到输出文件中, 生成最终打包好的文件

‍

# 配置webpack的打包发布

在`packge.json`文件的`script`节点下, 新增`build`命令如下

```js
    "scripts": {
        "server": "webpack serve",
        "dev": "webpack",
        "build": "webpack --mode production"
    },
```

注意: 通过`--`添加的参数, 会覆盖`webpack.config.js`中的配置

‍

## 自动清理输出目录中的文件

使用`cleanWebpackPlugin` 插件

```js
const { CleanWebpackPlugin } = require("clean-webpack-plugin");
const cleanWebpackPlugin = new CleanWebpackPlugin();
   
{
	 plugins: [htmlWebpackPlugin, cleanWebpackPlugin],
}

```

‍

# Source Map

## 什么是Source Map

SourceMap 就是一个信息文件, 里面存储着位置信息, 也就是说, SourceMap文件中存储着压缩混淆后的代码, 对应的转换前的位置

有了它, 出错的时候, 出错工具就能直接显示原始代码, 而不是转换行的代码, 极大的方便后期的调试

## 使用方法

在`webpack.config.js`中添加如下节点

```js
module.exports = {
    mode: "development", //指定构建模式， 可选值有development, production
    // devtool: "eval-source-map", //暴露源码和行号
    devtool: "nosources-source-map", //只暴露行号, 不暴露代码

```

‍

‍

# webpack中的alias别名

在`webpack.config.js`中添加如下节点

```js
module.exports = {
    	mode: "development", //指定构建模式， 可选值有development, production  
	resolve: {
        alias: {
            "@": path.join(__dirname, "src"),
        },
    },
}
```
