# 封装自己的Ajax函数

‍

```js
myAjax({
    method: "get",
    url: "http://www.liulongbin.top:3006/api/getbooks",
    data: {},
    success: function (e) {
        console.log(e);
    },
});
// myAjax({
//     method: "post",
//     url: "http://www.liulongbin.top:3006/api/addbook",
//     data: { bookname: "xxx", author: "xxx", publisher: "xxxx" },
//     success: function (e) {
//         console.log(e);
//     },
// });

function myAjax(configObj) {
    // let method = configObj.method;
    // let url = configObj.url;
    // let data = configObj.data;
    // let success = configObj.success;

    //可以使用解构赋值
    let {method,url,data,success}=configObj


    // 使用xhr发起请求
    let xhr = new XMLHttpRequest();
    if (method == "get") {
        xhr.open(method, url + "?" + resoveData(data));
        xhr.send();
    } else {
        xhr.open(method, url);
        xhr.setRequestHeader(
            "Content-Type",
            "application/x-www-form-urlencoded"
        );
        xhr.send(resoveData(data));
    }

    xhr.addEventListener("readystatechange", function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            let res = JSON.parse(xhr.responseText);
            success(res);
        }
    });
}

/**
 *
 * @param {object} data
 * @return {string}
 */
function resoveData(data) {
    //处理data对象, 将data转换为查询字符串
    let queryArr = [];
    let queryStr = "";
    for (const key in data) {
        if (Object.hasOwnProperty.call(data, key)) {
            const element = data[key];

            queryArr.push(key + "=" + element);
        }
    }
    queryStr = queryArr.join("&");
    console.log(queryStr);
    return queryStr;
}
```
