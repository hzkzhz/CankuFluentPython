# 把函数视作对象

### 一等函数
- 在运行时创建
- 能赋值给变量或数据结构中的元素
- 能作为参数传给函数
- 能作为函数的返回结果

### 通过别的名称使用函数，再把函数作为参数传递
```
def factorial(n):
    return 1 if n < 2 else n * factorial(n - 1)

fact = factorial
fact(5)
```

# 高阶函数
#### map、filter、reduce 和 apply
如果想使用`不定量`的参数调用函数，可以编写fn(*args, **keywords)，不用再编写apply(fn, args, kwargs)。




