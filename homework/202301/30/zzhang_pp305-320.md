# Fluent Python: pp 305 - 320

13.1

- 只能重载现有的，比如 &、|、~、==、!=、>、<、>=、<=、-、+、* etc
- 不能重载：is, and, or, not 和内置类型的运算符

13.2 一元运算符 -, +, ~,abs

- 得到参数 `self`，返回新对象
- `x != +x` 可能发生，当x是decimal且`ctx.prec` 精度变了的时候（`+x`会使用当前算术运算上下文的精度）

13.3 重载 +

- 数学运算加法，并给短的vector padding 0

    ```python
    def __add__(self, other): # other 是a+b右边的vector/tuple/... b
      try:
        pairs = itertools.zip_longest(self, other, fillvalue=0.0)
        # zip_logest 能处理任何**可迭代**对象
      except TypeError: # 不能相加 比如 int + str
        return NotImplemented
      return Vector(a + b for a, b in pairs)
    ```

    - 如果做操作数上加没法成功（返回`NotImplemented`），Python会尝试在右操作数上调用`__radd__`

    - 右操作数上的加使用 `__radd__`

        ```python
        def __radd__(self, other):
        	return self + other # 委托给 __add__
        ```

13.4 重载 *

```python
def __mul__(self, scalar):
  if isinstance(scalar, numers.Real):
    return Vector(n * scalar for n in self)
  else: # 让 Python 尝试在 scalar 操作数上调用 __rmul__ 方法
    return NotImplemented
def __rmul__(self, scalar):
  return self * scalar
```



13.5 比较运算符 

- 记得做类型检查

    ```python
    def __eq__(self, other):
      if isinstance(other, Vector):
        return (len(self) == len(other) and
               all (a == b for a,b in zip(self, other)))
      else:
        return NotImplemented
    ```

- `__ne__` 就是对`__eq__`取反
