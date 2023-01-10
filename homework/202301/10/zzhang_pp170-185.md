# Fluent Python: pp 170-185

#### 7.8.2 单分派泛函数 generic function

- 针对不同的数据类型提供不同的接口很麻烦 => 用 `functools.singledispatch` 装饰器 （`@singledispatch`）[普通函数 -> 泛函数]

    使用方法：

    ```python
    @singledispatch
    def htmlize(obj):
      ...
    
    @htmlize.register(str)
    def _(text): # 函数名称不重要
      ... # 针对text的实现
    
    @htmlize.register(number.Integral) # 尽可能用抽象基类，而不是具体实现比如int
    def _(n):
      ... # 针对int的实现
    
    @htmlize.register(tuple) # 叠多个register装饰器，一个函数支持不同类型
    @htmlize.register(abc.MutableSequence) # 用这个基类，而不是list
    def _(seq):
      ...
    ```

- 对 模块化扩展 友好

### 7.9 叠放装饰器

叠在上面的d1后做f = d1(d2(f))

### 7.10 参数化装饰器

7.10.1

- 定义装饰器函数的时候可以加parameter

7.10.2

- 有一个小点：clocked 函数定义了`fmt.format(**locals())` => 用 `**locals() ` 在 fmt 中引用 clocked 的局部变量
- 装饰器 最好通过实现 `__call__` 方法的类实现，不应该像本章的示例那样通过函数实现



## Ch 8 对象引用、可变性和垃圾回收

8.1

- 变量是贴标签

8.2

- `==` （`__eq__`）比较的是内容（对象中的数据）
- `is` 比较的是对象标识（id）

