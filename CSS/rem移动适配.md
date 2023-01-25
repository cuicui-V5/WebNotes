---
title: rem移动适配
date: 2022-07-17T20:07:45Z
lastmod: 2022-07-17T20:07:53Z
---

# rem移动适配

# rem单位

* 相对单位
* rem单位是相对于HTML标签的字号计算结果 . html标签又叫根标签
* 1rem=1HTML字号大小=1/10屏幕宽度

# 媒体查询

媒体查询能检测视口的宽度, 然后编写差异化的css样式

语法:

```html
@media( 媒体特性 ){
  选择器{css属性
  }
}


例如:

@media(width:375px){
  html{
      font-size:32px;
   }

}
```

# rem适配步骤

1. 确定设计稿对应的html标签字号

    1. 查看设计稿宽度 => 确定设备宽度 => 确定基准根字号 (1/10视口宽度)
2. rem单位的尺寸

    1. rem尺寸= px单位数值 / 基准根字号

# 如何使用flexible.js进行rem适配

不需要手动写媒体查询,只需要在body最后加入  
`<scriptsrc="./js/flexible.js">`
