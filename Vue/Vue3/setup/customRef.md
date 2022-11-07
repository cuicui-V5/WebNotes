# customRef

创建一个自定义的ref , 并对其依赖项跟踪和更新触发进行显示控制

语法: 

```js
        function myRef(val) {
            return customRef((track, trigger) => {
                return {
                    get() {
                        console.log("有人读取了myRef", val);
                        // 让get追踪val值的变化
                        track();
                        return val;
                    },
                    set(newVal) {
                        console.log("有人设置了myRef", newVal);
                        val = newVal;
                        // 通知vue更新页面
                        trigger();
                    },
                };
            });
        }
```

```js
    setup() {
        let keyWord = myRef("hello");
        let timer;
        function myRef(val) {
            return customRef((track, trigger) => {
                return {
                    get() {
                        console.log("有人读取了myRef", val);
                        // 让get追踪val值的变化
                        track();
                        return val;
                    },
                    set(newVal) {
                        console.log("有人设置了myRef", newVal);
                        val = newVal;
                        // 使用防抖策略
                        clearTimeout(timer);
                        timer = setTimeout(() => {
                            // 通知vue更新页面
                            trigger();
                        }, 600);
                    },
                };
            });
        }
        return {
            keyWord,
        };
    },
```

‍
