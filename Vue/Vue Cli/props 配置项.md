# props 配置项

# props 配置项

功能: 让组件接收外部传过来的数据

## 使用 props

### 传递数据

```html
<MyStudent name="小明" sex="男" />
```

### 接收数据

共有三种方式可以声明 `props`​

```js
  //   简单声明
  //   props: ["name", "age", "sex"],

  //   对象声明方式, 可以指定数据类型
  //   props: {
  //     name: String,
  //     age: Number,
  //     sex: String,
  //   },

  // 复杂对象声明方式, 可以指定数据类型, 是否必需, 默认值
  props: {
    name: {
      type: String,
      require: true,
    },
    age: {
      type: Number,
      default: 200, 
    },
    sex: {
      type: String,
      require: true,
    },
  },
```

注意: `props ​`是只读的, Vue 底层会检测你对 `props ​`的修改, 如果进行了修改, 就会发出警告, 若业务需求确实需要修改, 那么请复制 `props ​`的内容到 `data ​`中一份, 然后去修改 `data` 中的数据

‍

### 使用props的数据

在结构中直接写变量名

在脚本中使用`​ this.变量`

‍
