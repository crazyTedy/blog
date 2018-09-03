---
title: 通过原型继承创建一个新的对象（inherit函数）
date: 2018-06-12 13:12:04
tags: ['js']
---
### <!--more-->
## inherit函数
```js 
    function inherit(Obj){
		if(Obj === null) throw TypeError();
		// 如果Object上有create方法则执行 
		if(Object.create){
			return Object.create(Obj);
		}
		if(Obj !== 'object' && Obj !== 'function') throw TypeError();
        function f() {};
        f.prototype = Obj;
        return new f()
	}
    var a = { c:2 }
    inherit(a);
    console.log(inherit(a))
```