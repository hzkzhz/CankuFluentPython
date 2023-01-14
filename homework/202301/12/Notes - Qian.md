### reduce()
```
from functools import reduce

reduce(add, range(10)) # reduce(add, [0,1,2,3,4,5,6,7,8,9]) => initial value is 0 => 0 + 0, 0 + 1, 1 + 2, ..., 36 + 9
Output: 45
```

### 匿名函数
- lambda 函数的定义体只能使用纯表达式。
- lambda 函数的定义体中不能赋值，也不能使用while和try等语句。

### 可调用对象
判断对象能否调用，最安全的方法是使用内置的 callable() 函数

```
[callable(obj) for obj in (abs, str, 13)]
[True, True, False]
```

装饰器就是这样。装饰器必须是函数， 而且有时要在多次调用之间“记住”某些事 [ 例如备忘(memoization)，即缓存消耗大的 计算结果，供后面使用 ]。
创建保有内部状态的函数，还有一种截然不同的方式——使用闭包。
