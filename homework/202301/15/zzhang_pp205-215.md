# Fluent Python: pp 205-215

## Ch 9 符合Python风格的对象

9.1 对象表示形式

- `__repr__` 给开发者看的：比如会输出`Vector2d(3.0, 4.0)`
- `__str__` 给用户看的：比如在 `print(v1)` 时输出`(3.0,4.0)`
- `__bytes__` 返回字节序列表示
- `__format__` 会被内置的`format()` 函数和`str.format()` 方法调用

9.2 

- `__iter__` 让实例变成可迭代的对象，这样才能拆包，比如`x, y = my_vector`

- `__repr__`: 用`{!r}` 获取各个分量的表示形式

    - ```python
        def __repr__(self):
          class_name = type(self).__name__
          return '{}({!r}, {!r})'.format(class_name, *self)
        ```

    - 因为它的实例是可叠戴的对象，`*self` 会把 x 和 y分量提供给format 函数 

9.3 备选构造方法

- 从字节序列转化成`Vector2d`实例：用`array.array`里的`.frombytes`

    ```python
    @classmethod # 定义操作类，而不是实例的方法
    def frombytes(cls, octets): # 不用加self; cls 时传入的类本身
      typecode = chr(octets[0]) # 第一个字节是typecode
      memv = memoryview(octets[1:]).cast(typecode)
      return cls(*memv) # 构建了一个新实例
    ```

9.4 `classmethod` 和 `staticmethod`

- `classmethod` 定义操作类，而不是操作实例
    - 第一个参数是 **类本身**
    - 常见用途：定义备选构造方法
- `staticmethod` 改变方法 
    - 改变方法的调用方式，但是第一个参数**不是**特殊的值
    - 和普通函数差不多，只是在类的定义体中

9.5 格式化现实

`.format(my_obj, format_spec)`

- `format_spec`:
    - `0.4f` 保留四位小数
    - `'{rate:0.2f}'.format(rate=brl)` 2位小数，指明字段名称为rate
    - `b` 二进制
    - `x` 十六进制int
    - `.1%` 保留一位小数的百分数
- 如果是自己定义的类，需要实现`__format__` ，比如把每个x, y 都按fmt_spec的格式format一下再返回

9.6 可散列的Vector2d

- 自己写`__hash__`方法

- 实现“不可变”性：用`@property` 修饰器

    - ```python
        def __init__(self, x, y):
          self.__x = float(x) # 用两个前导下划线把属性标记为私有的
          
        @property
        def x(self):
        	return self.__x
        ```

        
