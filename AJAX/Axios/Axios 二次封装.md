---
title: Axios 二次封装
date: 2022-12-14T09:33:35Z
lastmod: 2022-12-20T21:17:38Z
---

# Axios 二次封装

axios的二次封装就是使用==拦截器==在请求之前或响应之前处理一些事情

首先使用`axios.create ​`​创建一个自定义`axios`​实例, 然后使用`interceptors.request`​或`interceptors.response`​来绑定请求拦截器或响应拦截器

```ts
import axios from "axios";
import nprogress from "nprogress";

const requests = axios.create({
    baseURL: "http://gmall-h5-api.atguigu.cn",
});

// 添加请求拦截器
requests.interceptors.request.use(
    function (config) {
        // 在发送请求之前做些什么
        console.log(config);
        // 开始进度条
        nprogress.start();
        return config;
    },
    function (error) {
        // 对请求错误做些什么
        console.log(error.message);
        nprogress.done();

        return Promise.reject(error);
    },
);

// 添加响应拦截器
requests.interceptors.response.use(
    function (response) {
        // 2xx 范围内的状态码都会触发该函数。
        // 对响应数据做点什么
        console.log(response.data);
        nprogress.done();

        return response;
    },
    function (error) {
        // 超出 2xx 范围的状态码都会触发该函数。
        // 对响应错误做点什么
        console.log(error.message);
        nprogress.done();

        return Promise.reject(error);
    },
);
export default requests;
```

# 接收的json中数字过长丢失精度问题

在axios的封装中使用响应转换器

```js
import jsonbig from "json-bigint";
const request = axios.create({
    transformResponse: (data) => {
        return jsonbig.parse(data);
    },
});
```
