# notes

看到 377 页，回顾一下 pattern matching class instances。

对于一个 sequence 来说，match 操作语法非常简单：

```python
match var:
    case [int(a), chr(b)]
        pass
```

这里就是尝试去 bind 这些变量，如果 bind 成功即 match 成功。

对于一个类来说，匹配到时候需要这样写：

```python
class City(typing.NamedTuple):
    country: str
    name: str

def match_china():
    results = []
    for city in cities:
        match city:
            case City(country='China', name=c):
                results.append(c)
```

回到377页，我们想要解决的是：如何提供一个 positional pattern match？也就是说我们想写：

```python
case Vector2d(_, 0):
```

这里有一个 _ 作为 positional argument。

这里想要实现这样一个操作只需要提供一个 __match_args__ class attribute 就可以了：

```python
class Vector2d:
    __match_args__ = ('x', 'y')
```

这里的 x 和 y 就是类的成员变量（或者叫 attribute）。