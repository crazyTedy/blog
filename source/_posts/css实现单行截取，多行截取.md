---
title: css实现单行截取，多行截取
date: 2018-06-12 15:42:14
tags: ['css']
---
### <!--more-->
### 多行文本溢出省略号                                 
``` css
    .text{
			width: 100%;
			height: 50px;
			display:-webkit-box;    
            //排列方向
			-webkit-box-orient: vertical;
            //规定第几行溢出加...
			-webkit-line-clamp: 2;   
            // 超出隐藏 
			overflow: hidden; 
		}
    注：只能在webkit或者移动端使用
```

### 单文本溢出省略号

``` css
    .text{
			width: 100%;
			height: 50px;
			overflow: hidden;
            white-space: nowrap;
			text-overflow: ellipsis;
		}
```
