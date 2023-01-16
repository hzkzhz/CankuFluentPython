#notes

函数是一个一等object，同时一个class也可以化身为一个函数，只需要我们提供 __call__ 函数即可。

函数的参数传递在 python 里面是非常灵活的。灵活性一定会失去一定的效率，因为我们必然在运行时的时候做了很多解包、匹配之类的事情。

python3 中引入 keyword-only arguments，它们不接受不具体给定名字的参数传递，比如：

```python
def f(a, *b, c):
    pass
```
那么这个 f 函数中的参数 c 就是不接受比如：
f(1, 2)
这样的情况。

在 py3.8 中又引入了 positional only。

