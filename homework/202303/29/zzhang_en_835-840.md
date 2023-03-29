# Fluent Python: pp 835 - 840

### Ch 22: Dynamic Attributes and Properties

Dynamic attributes:

- computed on demand

两种形式：

1. `@property` 装饰器
2. `__getattr__` special method

Exploring JSON-like Data with Dynamic Attributes

- `__getattr__` 只有在解释器没法retrieve the attribute的时候才会被调用

- 如果访问一个未定义的属性，应该raise `AttributeError` 而不是 `KeyError`
    - 实现的时候会尝试访问data的attribute（非keys)
        - `return getattr(self.__data, name)`

