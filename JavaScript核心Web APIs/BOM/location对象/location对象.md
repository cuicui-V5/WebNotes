# location对象

## 目录

*   [location对象](#location对象-1)

*   [URL :统一资源定位符](#url-统一资源定位符)

*   [location对象的属性](#location对象的属性)

*   [location对象的方法](#location对象的方法)

# location对象

window对象给我们提供了一个location属性用于获取或设置窗体的url, 并且可以用于解析[URL](../URL/URL.md "URL"), 因为这个属性返回的是一个对象, 所以我们也称为loaction对象

# URL :统一资源定位符

# location对象的属性

| location对象属性      | 返回值                |
| ----------------- | ------------------ |
| location.href     | 获取或设置整个url         |
| location.host     | 返回主机名(域名)          |
| location.port     | 返回端口号, 如果没写那么就为空字符 |
| location.pathname | 返回路径               |
| location.search   | 返回参数               |
| location.hash     | 返回片段               |

# location对象的方法

| location对象方法       | 含义                            |
| ------------------ | ----------------------------- |
| location.assign()  | 和href一样, 可以跳转页面 (也称为重定向)      |
| location.replace() | 替换当前页面, 因为不记录历史, 所以不能用后退按钮    |
| location.reload()  | 刷新页面, 相当于f5, 如果参数为true, 则强制刷新 |
