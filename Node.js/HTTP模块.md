# HTTP模块

‍

http 模块是 Node.js 官方提供的, 用来创建 web 服务器的模块, 通过 http 模块提供的 `http.creatServer()` 方法, 就能方便的把一台普通电脑,变成一台 Web 服务器, 从而对外提供 Web 资源服务

‍

# 导入 http

```js
const http = require("http")
```

‍

# 创建基本的 Web 服务器

## 创建 Web 服务器的基本步骤

1. 导入 `http ​`模块

    1. `const http = require("http")`
2. 创建 `web ​`服务器实例

    1. 调用`http.creatServer() ​`方法创建Web服务器实例
3. 为服务器实例绑定 `request ​`事件, 监听客户端的请求

    1. `server.on("request",(req,res)=>{console.log("someone visit our server")})`
4. 启动服务器

    1. 调用服务器实例的`​ listen() ​`方法, 启动服务器实例
    2. `server.listern(80,()=>{console.log("server start at 80 port")})`

‍

```js
//1. 导入http
const http = require("http");

//生成http对象

const server = http.createServer();

//绑定事件

server.on("request", function (req, res) {
    console.log("someone visit our server");
    console.log(req);
    console.log(res);
});

//启动wev服务器

server.listen(80, () => {
    console.log("server started ar 127.0.0.1");
});
```

## req请求对象

只要服务器接收到了客户端的请求, 就会调用通过`server.on()`绑定的`request`事件处理函数, 其中`req`为事件对象

常用属性:

* url : 请求的url
* method : 请求方式

‍

## res响应对象

在request事件处理函数中, 如果想访问和服务器有关的数据或属性, 可以使用res响应对象

### res.end()

响应并且结束请求

‍

‍

## 解决中文乱码问题

为了解决中文乱码问题, 需要手动设定响应头`Content-Type`为`text/html;charset=utf-8`

‍

```js
//1. 导入http
const { LOADIPHLPAPI } = require("dns");
const http = require("http");

//生成http对象

const server = http.createServer();

//绑定事件

server.on("request", function (req, res) {
    console.log("someone visit our server" + req.url + req.method);
    res.setHeader("Content-Type", "text/html;charset=utf-8");
    res.end("hello world 你好世界!");
});

//启动wev服务器

server.listen(80, () => {
    console.log("server started ar 127.0.0.1");
});
```

‍

# 根据不同的url相应不同的内容

## 核心实现步骤

1. 获取请求的`url`地址
2. 设置默认的相应内容为`404 ​`
3. 判断用户请求的是否为`/ ​`或 `index.html`
4. 判断用户请求的是否为`about.html`
5. 设置`Content-Type` 响应头, 防止中文乱码
6. 使用`res.end()`把内容相应给客户端

‍
