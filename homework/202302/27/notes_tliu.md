# notes

这里作者想要实现一个 slice 的功能。

本来其实我们就是可以 slice 的，只要我们提供了 __getitem__ 方法就可以传入一个 slice。

但是问题在于如果我们的 getitem 写的比较简单的话，比如直接返回 _components[index] 这就会导致我们 slice 得到的结果是一个 array 而不是一个新的 Vector。

那么我们能不能控制这个行为呢？肯定是可以的。
我们只需要在 getitem 的时候判断一下，

```python

def __getitem__(self, key):
    if isinstance(key, slice):
        cls = type(self)
        return cls(self.components[key])
    index = operator.index(key)
    return self.components[index]

```

在这里我们做的判断就是如果传入的 key 是一个 slice 变量就新构造一个 vector 出来。否则的话当成一般的 index 来理解，返回一个普通的元素。