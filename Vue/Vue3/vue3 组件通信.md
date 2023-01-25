---
title: vue3 组件通信
date: 2022-12-24T19:57:03Z
lastmod: 2022-12-24T19:59:08Z
---

# vue3 组件通信

Vue 3 应用实例不再实现事件触发接口，因此移除了 `$on`​ 、 `$off`​ 和 `$once`​ 这几个事件 API ，无法像 Vue 2 一样利用 Vue 实例创建 EventBus 。

‍

可以使用 [mitt](https://github.com/developit/mitt) 或者 [tiny-emitter](https://github.com/scottcorgan/tiny-emitter) 等第三方插件实现 EventBus 。

### 创建 Vue 3 的 EventBus[#](https://vue3.chengpeiquan.com/communication.html#%E5%88%9B%E5%BB%BA-vue-3-%E7%9A%84-eventbus-new)

这里以 mitt 为例，示范如何创建一个 Vue 3 的 EventBus ，首先需要安装它。

```
npm i mitt
```

然后在 src/libs 文件夹下，创建一个名为 eventBus.ts 的文件，文件内容和 Vue 2 的写法其实是一样的，只不过是把 Vue 实例换成了 mitt 实例。

‍

```
// src/libs/eventBus.ts
import mitt from 'mitt'
export default mitt()
```

接下来就可以定义通信的相关事件了，常用的 API 和参数如下：

|方法名称|作用|
| ----------| --------------------------------|
|on|注册一个侦听事件，用于接收数据|
|emit|调用方法发起数据传递|
|off|用来移除侦听事件|

​`on`​ 的参数：

|参数|类型|作用|
| ---------| ----------| --------------------------------------|
|type|string|symbol|
|handler|function|接收到数据之后要做什么处理的回调函数|

这里的 `handler`​ 建议使用具名函数，因为匿名函数无法销毁。

​`emit`​ 的参数：

|参数|类型|作用|
| ------| --------| ------------------------------|
|type|string|symbol|
|data|any|与 on 对应的，允许接收的数据|

​`off`​ 的参数：

|参数|类型|作用|
| ---------| ----------| -----------------------------------------|
|type|string|symbol|
|handler|function|要被删除的，与 on 对应的 handler 函数名|

更多的 API 可以查阅 [插件的官方文档](https://github.com/developit/mitt) ，在了解了最基本的用法之后，来开始配置一对组件通信。

### 创建和移除侦听事件[#](https://vue3.chengpeiquan.com/communication.html#%E5%88%9B%E5%BB%BA%E5%92%8C%E7%A7%BB%E9%99%A4%E4%BE%A6%E5%90%AC%E4%BA%8B%E4%BB%B6-new)

在需要暴露交流事件的组件里，通过 `on`​ 配置好接收方法，同时为了避免路由切换过程中造成事件多次被绑定，从而引起多次触发，需要在适当的时机 `off`​ 掉：

‍

```
import { defineComponent, onBeforeUnmount } from 'vue'
import eventBus from '@libs/eventBus'

export default defineComponent({
  setup() {
    // 声明一个打招呼的方法
    function sayHi(msg = 'Hello World!') {
      console.log(msg)
    }

    // 启用侦听
    eventBus.on('sayHi', sayHi)

    // 在组件卸载之前移除侦听
    onBeforeUnmount(() => {
      eventBus.off('sayHi', sayHi)
    })
  },
})
```

关于销毁的时机，可以参考 [组件的生命周期](https://vue3.chengpeiquan.com/component.html#%E7%BB%84%E4%BB%B6%E7%9A%84%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F-new) 。

### 调用侦听事件[#](https://vue3.chengpeiquan.com/communication.html#%E8%B0%83%E7%94%A8%E4%BE%A6%E5%90%AC%E4%BA%8B%E4%BB%B6-new)

在需要调用交流事件的组件里，通过 `emit`​ 进行调用：

‍

```
import { defineComponent } from 'vue'
import eventBus from '@libs/eventBus'

export default defineComponent({
  setup() {
    // 调用打招呼事件，传入消息内容
    eventBus.emit('sayHi', 'Hello')
  },
})
```
