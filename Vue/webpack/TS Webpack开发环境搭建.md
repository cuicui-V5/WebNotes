---
title: TS Webpack开发环境搭建
date: 2022-11-08T19:49:25Z
lastmod: 2022-11-10T10:00:40Z
---

# TS Webpack开发环境搭建

‍

# webpack

## 安装依赖

​`npm i -D webpack webpack-cli webpack-dev-server typescript ts-loader clean-webpack-plugin html-webpack-plugin`​

## 初始化项目packge.json

​`npm init -y`​

加入以下内容

```js
    "scripts": {
        "build": "webpack",
        "serve": "webpack serve --open"
    },
```

配置`webpack.config.js`​

```js
// 引入插件
const path = require("path");
const htmlPlugin = require("html-webpack-plugin");
const { CleanWebpackPlugin } = require("clean-webpack-plugin");
module.exports = {
    // 入口文件
    entry: "./src/index.ts",
    // 输出设置
    output: {
        // 输出路径
        path: path.resolve(__dirname, "dist"),
        filename: "bundle.js",
        // 关闭箭头函数
        environment: {
            arrowFunction: false,
        },
    },
    // 生产模式
    mode: "production",
    // 打包的拓展名
    resolve: {
        extensions: [".ts", ".js"],
    },
    module: {
        rules: [
            {
                test: /\.ts$/,
                use: [
                    {
                        loader: "babel-loader",
                        options: {
                            presets: [
                                [
                                    "@babel/preset-env",
                                    {
                                        targets: {
                                            chrome: "88",
                                            ie: 11,
                                        },
                                        corejs: "3",
                                        useBuiltIns: "usage",
                                    },
                                ],
                            ],
                        },
                    },
                    "ts-loader",
                ],
                exclude: /node_modules/,
            },
        ],
    },
    // 插件
    plugins: [
        new htmlPlugin({
            template: "./src/index.html",
        }),
        new CleanWebpackPlugin(),
    ],
};
```

# babel 配置

## 安装依赖

`npm i -D @babel/core @babel/preset-env babel-loader core-js`​

‍
