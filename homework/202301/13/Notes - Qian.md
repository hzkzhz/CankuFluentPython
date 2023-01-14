# cls
使用名为 cls 的关键字参数传入“class”属性，这是一种变通方法，因为“class”是Python的关键字

```
def tag(cls=None, **attrs):
    if cls is not None:
        attrs['class'] = cls # the value of attrs is a class
```

