---
title: WebSocket
date: 2022-11-15T22:00:40Z
lastmod: 2022-11-16T20:28:21Z
---

# WebSocket

‍

# ws客户端的基本使用

```js
var ws = new WebSocket("wss://echo.websocket.org");

ws.onopen = function(evt) { 
  console.log("Connection open ..."); 
  ws.send("Hello WebSockets!");
};

ws.onmessage = function(evt) {
  console.log( "Received Message: " + evt.data);
  ws.close();
};

ws.onclose = function(evt) {
  console.log("Connection closed.");
};  
```

## 新建实例

```js
var ws = new WebSocket('ws://localhost:8080');
```

注意:

* 不能catch住websocket的超时error的

‍

‍

### webSocket.readyState

返回实例的当前状态

```js
CONNECTING：值为0，表示正在连接。
OPEN：值为1，表示连接成功，可以通信了。
CLOSING：值为2，表示连接正在关闭。
CLOSED：值为3，表示连接已经关闭，或者打开连接失败。
```

### webSocket.onopen

实例对象的`onopen`​属性，用于指定连接成功后的回调函数。

```js
ws.addEventListener('open', function (event) {
  ws.send('Hello Server!');
});
```

### webSocket.onclose

实例对象的`onclose`​属性，用于指定连接关闭后的回调函数。

```js
ws.addEventListener("close", function(event) {
  var code = event.code;
  var reason = event.reason;
  var wasClean = event.wasClean;
  // handle close event
});
```

### webSocket.onmessage

实例对象的`onmessage`​属性，用于指定收到服务器数据后的回调函数。

```js
ws.addEventListener("message", function(event) {
  var data = event.data;
  // 处理数据
});
```

### webSocket.send()

实例对象的`send()`​方法用于向服务器发送数据。

```js
ws.send('your message');
```

## webSocket.onerror

实例对象的`onerror`​属性，用于指定报错时的回调函数。

```js
socket.addEventListener("error", function(event) {
  // handle error event
});
```

# ws服务器端

首先引入`ws`​模块, 然后与客户端类似, 新建socket实例

使用`socket.send()`​发送数据

使用 `socket.addEventListener("message", ({data}) => {})`​或`socket.on("messgae",()=>{})`​ 接收数据

```js
import { WebSocketServer } from "ws";
const server = new WebSocketServer({ port: 1234 });

server.on("connection", (socket) => {
    // 向客户端发送消息
    socket.send(
        JSON.stringify({
            msg: "hello from server",
            code: "200",
        }),
    );

    // 从客户端接收消息
    socket.on("message", (data) => {
        console.log(data);
        const packet = JSON.parse(data);
        console.log(packet);
    });

    socket.addEventListener("message", ({data}) => {
        console.log(data);
    });
});
```

‍

## 获取所有连接

每个ws连接都为一个独立的`socket`​实例

使用`server.clients`​列出所有连接

向每个连接广播消息: 

```js
const boardCast = () => {
    dataObj.onlineUser = ws.clients.size;
    ws.clients.forEach((client) => {
        client.send(JSON.stringify(dataObj));
    });
};
```
