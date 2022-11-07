# jQuery效果

# 显示隐藏效果

* 显示: `show([[speed],[easing],[callback]])`
* 隐藏: `hide([[speed],[easing],[callback]])`
* 切换: `toggle([[speed],[easing],[callback]])`

* 参数都可以省略, 无动画直接省略
* speed: 三种预定速度之一的字符串: "slow", "nomal", "fast"
* easing: 指定切换效果, 默认值"swing", 可用参数"linear"
* callback: 回调函数, 在动画完成时执行的函数, 每个元素执行一次

‍

# 滑动效果

* 上滑: `slideUp([speed],[easing],[callbcak]);`
* 下滑:`slideDown([speed],[easing],[callbcak]);`
* 切换:`slideToggle([speed],[easing],[callbcak]);`

* 参数都可以省略, 无动画直接省略
* speed: 三种预定速度之一的字符串: "slow", "nomal", "fast"
* easing: 指定切换效果, 默认值"swing", 可用参数"linear"
* callback: 回调函数, 在动画完成时执行的函数, 每个元素执行一次

# Hover效果

`hover([over],[out])`

* over : 鼠标移动到元素上要触发的函数 (相当于mouseenter)
* out: 鼠标移出元素要触发的函数(相当于mouseleave)
* ==如果只写一个参数, 那么鼠标经过和离开都会触发这个函数==

# 动画队列及其停止排队方法

动画或效果一旦触发就会执行, 如果多次触发, 就造成多个动画或者效果排队执行

### 停止排队

`stop();`

* `stop()`方法用于停止动画或效果
* 注意: `stop()`写到动画或效果的前面, 相当于结束上一次的动画

‍

# 淡入淡出效果

* `fadeIn([speed],[easing],[callbcak]);`
* `fadeOut([speed],[easing],[callbcak]);`
* `fadeToggle([speed],[easing],[callbcak]);`

* 参数都可以省略, 无动画直接省略
* speed: 三种预定速度之一的字符串: "slow", "nomal", "fast"
* easing: 指定切换效果, 默认值"swing", 可用参数"linear"
* callback: 回调函数, 在动画完成时执行的函数, 每个元素执行一次

`fadeTo([speed],opacity,[easing],[callbcak]);`

opacity: 透明度 必填, 取值范围0-1

speed : 速度 必填

‍

# 自定义动画

`animate(params,[speed],[easing],[fn])`;

参数: 

* params 要修改的样式, 以对象形式传递 必填

* speed: 三种预定速度之一的字符串: "slow", "nomal", "fast"
* easing: 指定切换效果, 默认值"swing", 可用参数"linear"
* callback: 回调函数, 在动画完成时执行的函数, 每个元素执行一次
