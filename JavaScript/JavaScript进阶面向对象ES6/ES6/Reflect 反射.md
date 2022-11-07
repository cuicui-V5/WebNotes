# Reflect 反射

通过反射可以取代直接调用Object上的方法

```js
            const p = new window.Proxy(person, {
                get(target, propName) {
                    console.log("读取了" + propName);
                    // return target[propName];
                    return Reflect.get(target, propName);
                },
                set(target, propName, val) {
                    console.log("修改或新增了" + propName);
                    // target[propName] = val;
                    Reflect.set(target, propName, val);
                    return target[propName];
                },
                deleteProperty(target, propName) {
                    console.log("删除了" + propName);
                    // return delete target[propName];
                    return Reflect.deleteProperty(target, propName);
                },
            });
```

‍
