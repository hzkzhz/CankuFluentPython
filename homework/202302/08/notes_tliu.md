# notes

原来上一次笔记中写的那样的 decorator factory 实际上并不是最好的写法，理论上来说我们应该写一个类，然后这个类提供一个 __call__ 方法。这样就可以实现一个类似于 functor 一样的东西。

只需要这样写就可以实现一个带有参数的 decorator：

```python
class clock:

    def __init__(self, fmt=DEFAULT_FMT):

        self.fmt = fmt

    def __call__(self, func):

        def clocked(*_args):
            t0 = time.perf_counter()
            _result = func(*_args)

            elapsed = time.perf_counter() - t0
            name = func.__name__
            args = ', '.join(repr(arg) for arg in _args) 
            result = repr(_result) 
            print(self.fmt.format(**locals()))   
            return _result 
        return clocked
```