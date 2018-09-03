---
title: webpack优化打包manifest.json报错
date: 2018-07-04 12:04:18
tags: ['js']
---

### <!--more-->

## webpack.dll.config.js 生成静态包的时候manifest.json 有时候回报一个错，提示格式有错误

```
Uncaught SyntaxError: Unexpected token :

```

## 具体解决办法是什么呢？

    在manifest.json中为内容添加 【】 包裹 
```
    [  manifest.json的内容 ]

```

    这样错误就会消失
