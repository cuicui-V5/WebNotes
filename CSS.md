---
title: CSS
date: 2022-07-17T20:03:08Z
lastmod: 2022-07-17T20:03:25Z
---

# CSS

CSS: 层叠样式表 Cascading style sheets

用来在网页中显示样式

写在哪里?  
css写在style标签中, style标签一般写在head标签里面, title标签下面  
怎么写?

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        p {
            color: aqua;
            font-size: 40px;
            background-color: cadetblue;
            width: 400px;
            height: 100px;
        }
    </style>
</head>

<body>
    <p>1234567</p>
</body>

</html>
```
