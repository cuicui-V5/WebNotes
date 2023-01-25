---
title: Vue3中的vue router
date: 2022-12-12T22:14:39Z
lastmod: 2022-12-12T22:15:01Z
---

# Vue3中的vue router

因为我们在 `setup`​ 里面没有访问 `this`​，所以我们不能再直接访问 `this.$router`​ 或 `this.$route`​。作为替代，我们使用 `useRouter`​ 函数：

```js
import { useRouter, useRoute } from 'vue-router'

export default {
  setup() {
    const router = useRouter()
    const route = useRoute()

    function pushWithQuery(query) {
      router.push({
        name: 'search',
        query: {
          ...route.query,
        },
      })
    }
  },
}
```
