# 909以后 python元编程-使用元类控制实例的创建
 - 问题的提出：在某些应用中，可能需要知道类的属性定义的顺序。例如，对初始化CSV 文件的库来说，需要保证每个字段传入的值符合类型。
 - 问题的解决：使用特殊方法__prepare__。__prepare__ 方法的第一个参数是元类，随后两个参数分别是要构建的类的名称和基类组成的元组，返回值必须是映射。元类构建新类时，__prepare__ 方法返回的映射会传给__new__ 方法的最后一个参数，然后再传给 __init__ 方法
 - 示例：某个初始化CSV文件的功能，三个字段依次是str、int和float：
```python3
from collections import OrderedDict
# A set of descriptors for various types
class Typed:
    _expected_type = type(None)
    def __init__(self, name=None):
        self._name = name

    def __set__(self, instance, value):
        if not isinstance(value, self._expected_type):
            raise TypeError('Expected ' + str(self._expected_type))
        instance.__dict__[self._name] = value

class Integer(Typed):
    _expected_type = int

class Float(Typed):
    _expected_type = float

class String(Typed):
    _expected_type = str

# Metaclass that uses an OrderedDict for class body
class OrderedMeta(type):
    def __new__(cls, clsname, bases, clsdict):
        d = dict(clsdict)
        order = []
        for name, value in clsdict.items():
            if isinstance(value, Typed):
                value._name = name
                order.append(name)
        d['_order'] = order
        return type.__new__(cls, clsname, bases, d)

    @classmethod
    def __prepare__(cls, clsname, bases):
        return OrderedDict()
 
 # 初始化CSV
 class Structure(metaclass=OrderedMeta):
    def as_csv(self):
        return ','.join(str(getattr(self,name)) for name in self._order)

# Example use
class Stock(Structure):
    name = String()
    shares = Integer()
    price = Float()

    def __init__(self, name, shares, price):
        self.name = name
        self.shares = shares
        self.price = price
```

    
    
    ```shell
    # 在交互环境中，打印如下：
    >>> s = Stock('GOOG',100,490.1)
    >>> s.name
    'GOOG'
    >>> s.as_csv()
    'GOOG,100,490.1'
    >>> t = Stock('AAPL','a lot', 610.23)
    Traceback (most recent call last):
        File "<stdin>", line 1, in <module>
        File "dupmethod.py", line 34, in __init__
    TypeError: shares expects <class 'int'>
    >>>
    ```
