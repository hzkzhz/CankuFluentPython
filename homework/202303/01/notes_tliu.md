# notes

在上一个例子的基础上作者又进化了一下 vector 这个类。之前我们的 x y z 变量（或者叫 attribute）声明为 private attribute。这个写法不如：

```python

__match_args__ = ('x', 'y', 'z', 't')

def __getattr__(self, name):
    cls = type(self)
    try:
        pos = cls.__match_args__.index(name)
    except ValueError:
        pos = -1
    if 0 <= pos < len(self._components):
        return self._components[pos]
    msg = f'{cls.__name__!r} object has no attribute {name!r}'
    raise AttributeError(msg)
```

这个写的就非常的漂亮了。首先肯定是不能修改的，其次 xyzt 会自动去找对应的纬度上的值。

getattr 这个函数只有在找不到本体上的这个变量，在父类中也找不到的时候才会调用。所以如果被截胡了就不行了。

但是这里还是有一个问题。就是虽然值不会被修改，但是可能会出现：

```python

v = Vector(range(5))
v.x = 10

```

这里需要注意我们并没有修改 v[0] 的值，但是我们给 v 创建了一个变量叫做 x 。以后再访问 v.x 的时候就会访问这个被创建的变量。

不必担心，可以通过定义 setattr method 来实现修改 attribute 的逻辑：

```python
def __setattr__(self, name, value):
    cls = type(self)
    if len(name) == 1:
        if name in cls.__match_args__:
            error = 'readonly attribute {attr_name!r}'
        elif name.islower():
            error = "can't set attributes 'a' to 'z' in {cls_name!r}"
        else:
            error = ''
        if error:
            msg = error.format(cls_name=cls.__name__, attr_name=name)
            raise AttributeError(msg)
    super().__setattr__(name, value)
```