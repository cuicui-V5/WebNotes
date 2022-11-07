# ref属性

# ref 属性

被用来给元素或子组件注册引用信息 (id 的替代者)

应有的 html 标签获取的是真实 DOM 元素, 应用在组件标签上是组件实例对象(vc)

# 

## ref 属性的使用

```html
<!--  打标签 -->
<h1 ref="h1">hello Vue!</h1>

<!--  使用 -->
console.log(this.$refs);
```

‍
