---
title: 动态组件 &lt;component&gt;
date: 2022-11-15T20:46:33Z
lastmod: 2022-11-15T21:43:04Z
---

# 动态组件 <component>

可以使用`<component> <component/>`​ 来动态的切换标签, 效果类似路由

使用 `is`​ 来指定要显示的组件, `is`​内的内容可以是组件实例或组件名

```js
 <component :is="tabs[currentTab]" class="tab"></component>
```

‍
