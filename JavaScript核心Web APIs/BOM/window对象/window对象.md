# window对象

## 目录

*   [window对象](#window对象-1)

*   [window对象的属性](#window对象的属性)

    *   [页面被卷去的部分scrollX scrollY](#页面被卷去的部分scrollx-scrolly)

*   [window对象的方法](#window对象的方法)

    *   [scrollTo todo](#scrollto-todo)

    *   [scroll()方法](#scroll方法)

*   [窗口加载事件](#窗口加载事件)

    *   [window.addeventListener("load",fun)](#windowaddeventlistenerloadfun)

    *   [window.addEventListner("pageshow",fun)](#windowaddeventlistnerpageshowfun)

        *   [事件对象](#事件对象)

    *   [document.addEventListner("DOMContentLoaded",fun)](#documentaddeventlistnerdomcontentloadedfun)

*   [调整窗口大小事件](#调整窗口大小事件)

    *   [onresize](#onresize)

# window对象

window对象是浏览器的顶级对象, 它具有双重角色

*   他是JS访问浏览器窗口的一个接口

*   他是一个全局对象, 定义在全局作用域内的变量, 函数都会变成window对象的属性和方法

在调用的时候可以忽略window, 前面学习的对话框都属于window对象方法, 如alert, prompt

注意: window下的一个特殊属性window\.name

# window对象的属性

window\.name

## 页面被卷去的部分scrollX scrollY

通过`scrollX scrollY` 可以获取页面在浏览器窗口中被卷去的部分

注意 :&#x20;

*   `scrollX scrollY`还有一个别名 `pageXOffset pageYOffset`

*   `document.documentElement.scrollTop window.scrollY window.pageYOffset `三者等价

# window对象的方法

## scrollTo todo

## scroll()方法

`window.scroll(x,y)`&#x20;

可以滚动到指定的坐标, 无动画

# 窗口加载事件

## window\.addeventListener("load",fun)

```javascript
window.onload = function(){} //或
window.addEventListner("load",fun)
```

`window.onload`是窗口(页面)加载事件, 当文档所有内容完全加载完毕(包括图像, 脚本文件, css文件等)就调用处理函数, 会比较慢

注意:

*   有了`onload`就可以把脚本写到页面元素的上方, 因为`onload`等页面内容全部加载完毕, 再去执行处理函数

*   `window.onload`只能写一次,如果写多次, 会被后面写的覆盖

*   如果使用`addEventListner`就没有限制

*   会触发load的三种情况

    *   超链接

    *   页面刷新

    *   页面前进后退

    *   **但是在firefox中, 前进后退不会触发load事件, 可以使用pageshow时间代替**

## window\.addEventListner("pageshow",fun)

`pageshow`事件会在页面显示时触发, 可以解决`firefox` 前进后退时不触发`load`事件的问题

### 事件对象

`e.persisted` 取值为`true /fasle` 如果页面来自于页面缓存, 那么返回`true`, 否则为`false`

## document.addEventListner("DOMContentLoaded",fun)

```javascript
document.addEventListner("DOMContentLoaded",fun)
```

`DOMContentLoaded` 当DOM加载完成后(不包括CSS样式表, 图片等),就触发

*   当页面图片很多时, 从用户访问到onload触发可能需要较长时间, 交互效果就不能实现, 会影响用户的体验, 此时使用`DOMContentLoaded` 就比较合理

*   `DOMContentLoaded` 比 `onload `更早触发

# 调整窗口大小事件

## onresize

```javascript
window.onresize
window.addEventListner("resize",fun)
```

`window.onresize`是浏览器窗口大小调整事件, 当窗口发小发生变化时就会触发

注意:

*   可以使用`window.innerWidth`和`window.innerHeight`获取当前的窗口大小
