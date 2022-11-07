# watch

监视属性: 

语法: `watch(target,handler,option)`​

* 当`target`​是`ref`​对象时, 可以正常获取`oldValue`​, 但是`reactive`​对象不能
* 如果需要监视多个数据, 那么将数据放入数组内即可
* 如果监视`reactive`​对象, 那么强制开启了深度监视, `deep`​配置项无效
* 如果需要监视`reactive`​对象内的某个属性, 那么需要把该属性放入函数内 `() => person.name`​, 此时也可以用数组

‍

‍

‍

```js
        // 1. 监视单个ref类型的数据
        watch(
            num1,
            (newVal, oldVal) => {
                console.log("数据发生改变", newVal, oldVal);
            },
            { immediate: true }
        );

        // 2. 监视多个ref数据, 放进数组内
        watch(
            [num1, num2],
            (newValArr, oldValArr) => {
                console.log("数据发生改变", newValArr, oldValArr);
            },
            { immediate: true }
        );

        // 3. 监视reactive对象内全部数据
        // 注意: 无法获取oldVal, 强制开启了深度监视
        watch(person, (newVal, oldVal) => {
            console.log("person发生改变", newVal, oldVal);
        });

        // 4. 监视reactive对象内某个属性, 将该属性写入函数内! 注意: 此时可以获取oldVal
        watch(
            () => person.name,
            (newVal, oldVal) => {
                console.log("person发生改变", newVal, oldVal);
            }
        );

        // 5.监视reactive对象内某些属性, 将包含该属性的函数放入一个数组内, 注意: 此时可以获取oldVal
        watch([() => person.name, () => person.age], (newVal, oldVal) => {
            console.log("person发生改变", newVal, oldVal);
        });
```

‍
