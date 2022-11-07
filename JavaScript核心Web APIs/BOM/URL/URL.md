# URL

统一资源定位符(Uniform Resource Locator:URL)  是互联网上标准资源的地址, 互联网上每个文件都有自己的URL, 它包含的信息指出文件的位置以及浏览器应该怎么处理它.

语法:

```javascript
protocol://host[:port]/path/[?query]#fragment
https://baidu,con/login/?name=tim&age=18#link
```

| 组成       | 说明                        |
| -------- | ------------------------- |
| protocol | 通信协议, 常见的有http,ftp,milto等 |
| host     | 主机名(域名)                   |
| port     | 端口号, 如果省略那么则为协议的默认端口号     |
| path     | 文件路径, 表示目录或文件             |
| query    | 参数, 采用键值对的形式, 多个参数用&间隔    |
| fragment | 片段, 一般是链接, 锚点等            |
