---
title: scoped 属性 lang 属性
date: 2022-10-12T14:35:17Z
lastmod: 2022-10-12T14:38:10Z
---

# scoped 属性 lang 属性

scoped 属性:   让样式在局部生效, 防止冲突

lang 属性: 指定样式所使用的语言 (需要安装对应的webpack loader)

写法: 

```html
<style  scoped lang="less">
#school {
    color: violet;

    font-size: 20px;
}
</style>
```

‍
