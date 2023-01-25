---
title: URL
date: 2022-07-17T21:34:20Z
lastmod: 2022-10-27T10:42:52Z
---

# URL

统一资源定位符(Uniform Resource Locator:URL)  url是互联网上标准资源的地址, 互联网上每个文件都有自己的URL, 它包含的信息指出文件的位置以及浏览器应该怎么处理它.

语法:

```JavaScript
protocol://host[:port]/path/[?query]#fragment
https://baidu,con/login/?name=tim&age=18#link
```

|||
| ----------| -----------------------------------------------------------|
|组成|说明|
|protocol|通信协议, 常见的有http,ftp,milto等|
|host|主机名(域名)|
|port|端口号, 如果省略那么则为协议的默认端口号|
|path|文件路径, 表示目录或文件|
|query|查询字符串[^1], 又叫参数, 采用键值对的形式, 多个参数用&间隔|
|fragment|片段, 一般是链接, 锚点等|

[^1]: # 查询字符串

    查询字符串(url参数)是指在url的末尾加上用于向服务器发送信息的字符串(变量)

    格式: 

    将英文的`?` 放在url的末尾, 然后加上 `参数=值` , 像加上多个参数的话, 就用`&`进行分隔

    `http://www.liulongbin.top:3006/api/getbooks?id=1`

    ## get请求携带参数的本质

    无论使用`$.ajax`, 还是使用`$.get` 又或者直接使用xhr对象发起get请求, 当需要携带参数的时候,  ==本质上, 都是直接将参数以查询字符串的形式, 追加到url地址的后面==

    ‍
