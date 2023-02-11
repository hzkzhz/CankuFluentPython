# notes

For a library or framework to be Pythonic is to make it as easy and natural as possible
for a Python programmer to pick up how to perform a task.

如何写出 Python 味的代码? 我写的代码一股 C++ 风, 需要好好学习一手.

这一章讲如何写一个库, 使得用这个库的人舒服一点, 让这个库 Pythonic 一点.

原来 Python 的类是没有真正的 private 函数的. redux 冗余.

因为 Python 变量是没有类型的, 所以很容易写出来意想不到的 feature/bug. 比如例子里的代码:

```python
def __eq__(self, other):
    return tuple(self) == tuple(other)
```

虽然在这个例子里我们是想比较 Vector 和 Vector 之间是否相等. 但是这样写的话所有能被 tuple 化的变量其实都可以和 Vector 进行比较. 这并不是我们的本意.