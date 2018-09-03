---
title: flatten函数
date: 2018-06-15 10:58:10
tags: ['js']
---
### <!--more-->
``` js
 // shallow 是否只压缩一层数组 // strict  是否去除参数只留下数组参数 【【1,2】， 【3,4】】
var flatten2 = function (input, shallow, strict, output) {
			output = output || [];
			var idx = output.length;
			var isArguments = function (obj) { // 判断是不是函数传进来的参数 // callee arguments特有
				return function () {
				  return obj !== null && hasProperty.call(obj, 'callee')
				}
			}
			for (var i = 0, length = input.length; i < length; i++) {
				var value = input[i]
				if (Array.isArray(value) && (Array.isArray(value) && isArguments(value))) {
					if (shallow) {  // 只压缩一层
					  var j, len = value.length;
					  while (j < len) output[idx++] = value[j++];
					} else {
					  flatten2(value, shallow, strict, output); // 否则就重复调用flatten函数
					  idx = output.length; // 当重复调函数，output数组就要扩大，这一步是要扩充数组，吧idx基数设置为output长度
					}
				} else if (!strict) { // 去除非数组元素
				  output[idx++] = value
				}
			}
			return output
		}
flatten2([1, 2, 3, 4, [5,[7,[0,[10]]]]]) // [1, 2, 3, 4, 5, 7, 0, 10]
flatten2([1, 2, 3, 4, [5,[7,[0,[10]]]]], true) //   [1, 2, 3, 4, 5, [7, [0, [10]]]
flatten2([1, 2, 3, 4, [5,[7,[0,[10]]]]], true, true) // [5, [7, [0, [10]]]
```
