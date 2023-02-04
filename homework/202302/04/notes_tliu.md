# notes

这里介绍了一个例子，我们想要实现一个 dispatch 的效果，对于不同的参数类型，有不同的输出结果。但是不希望使用 cpp 或者是 java 那样的编译期就需要决定类型，对不同的数据类型都重载一下这个函数，而是在运行时判断类型。直接用 if else 这样的方式，那么可扩展性不是很好，而且很笨重，随着时间推移，这个函数会越写越长，充满了if else。

在这里作者推荐使用 singledispatch 这个装饰器：

```python
@singledispatch
def htmlize(obj: object) -> str:
    content = htnl.escape(repr(obj))
    return f'<pre>{content}</pre>'

@htmlize.register
def _(text: str) -> str:
    content = html.escape(text).replace('\n','<br/>\n')

@htmlize.register
def _(seq:abc.Sequence) -> str:
    inner = '<li>\n<li>'.join(htmlize(item) for item in seq)
    pass
```

base 函数就是我们用 @singledispatch 装饰的 htmlize 函数。它的特化函数就是用 @htmlize.register 来装饰，也就是 base 函数的名字 + .register。

