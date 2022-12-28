# Fluent Python: pp 117-125

## Ch 5: 一等函数

函数是一等对象，满足：

- 在运行时创建
- 能赋值给变量或数据结构中的元素
- 能作为参数传给函数
- 能作为函数的返回结果

### 5.1 把函数视作对象

1. 可以加doc

   ```python
   def factorial(n):
     	'''returns n!'''
       return 1 if n < 2 else n * factorial(n-1)
   >>> factorial.__doc__ # 'return n!'
   >>> help(factorial) 
   # factorial(n)
   #    returns n!
   ```

2. 赋值给一个变量，作为参数传给map

   ```python
   fact = factorial
   map(factorial, range(11))
   ```

### 5.2 高阶函数 high-order function

- definition：接受函数为参数，或者把函数作为结果返回的函数，比如map, sorted

#### map, filter 和 reduce 的现代替代品

- 列表推导或生成器表达式具有 map 和 filter 两个函数的功能，而且 更易于阅读

例子：

```python
# example 1: 0-6的阶乘
>>> list(map(fact, range(6)))
>>> [fact(n) for n in range(6)] # 更好

# example 2: 1，3，5的阶乘
>>> list(map(factorial, filter(lambda n: n%2, range(6))))
>>> [factorial(n) for n in range(6) if n % 2] # 更好
```

reduce是内置函数，但是在 Python 3 中放到 functools 模块里了。这个函数最常用于求和，但最好用的是`sum` 函数

```python
# 之前
>>> from functools import reduce
>>> from operator import add
>>> reduce(add, range(100))

# 现在
>>> sum(range(100))
```



### 5.3 匿名函数 lambda

- 纯表达式，不能赋值、while、try等Python语句

- lambda 句法只是语法糖:与 def 语句一样，lambda 表达式**会**创建函数对象



### 5.4 可调用对象

- 判断是否可调用： `callable()`
- 其他都比较常见（类、定义了`__call__`的类的实例、方法等），生成器函数的实例也可以作为函数调用：调用生成器函数返回的是生成器对象。



### 5.5 用户定义的可调用类型

- 实现`__call__()` 即可
  - 实现 `__call__` 方法的类是创建函数类对象的简便方式，此时必须在内部维护一个状态，让它在调用之间可用

- 装饰器就是这样（后面讲）
- 创建保有内部状态的函数，还可以用闭包（后面讲）



### 5.6 函数内省

- 函数使用 `__dict__ `属性存储赋予它的用户属性

- 函数专有而用户定义的一般对象没有的属性

`__annotations__`: 参数和返回值的注解 (dict)

 `__call__`: 实现 () 运算符;即可调用对象协议 (method-wrapper)

 `__closure__`: 函数闭包，即自由变量的绑定(通常是 None) (tuple)

 `__code__`: 编译成字节码的函数元数据和函数定义体 (code)

`__defaults__`: 形式参数的默认值 (tuple)

`__get__`: 实现只读描述符协议 (method-wrapper)

`__globals__`: 函数所在模块中的全局变量 (dict)

`__kwdefaults__`: 仅限关键字形式参数的默认值 (dict)

 `__name__`: 函数名称 (str)

`__qualname__`: 函 数 的 限 定 名 称， 如 Random.choice (str)

