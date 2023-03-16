# notes

在以前的 python 中，我们不能构造一个 built in 类型的子类，比如说 list 或者是 map 类之类的。

这个的原因是：

Officially, CPython has no rule at all for when exactly overridden method of subclasses of built-in types get implicitly called or not. As an approximation, these methods are never called by other built-in methods of the same object. For example, an overridden __getitem__() in a subclass of dict will not be called by e.g. the built-in get() method.

这个是说比如我们继承了 dict 类，然后写了一个子类。现在这个子类重载了 getitem 函数。但是这并不代表你的子类的 get 函数就会调用 getitem 函数，也就是说你重载并没有用。

dict 类因为是一个 builtin 类，为了效率方面的考量，一般都用的是自己写的 C 函数。所以它 get 函数并不会调用 getitem 函数，所以你重载这个 getitem 并没有用。

作者在这里提供了一个例子：

```python
class DoubleDict(dict):
    def __setitem__(self, key, value):
        super().__setitem__(key, [value] * 2)

dd = DoubleDict(one=1)
dd['two'] = 2
dd.update(three=3)
```

在上面这个例子里面只有第二个才会调用新的 setitem 函数。
