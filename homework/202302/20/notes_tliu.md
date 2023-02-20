# notes

我们在 cpp 里有 static 函数，实现的功能是给一个类提供一个函数，而不是为每一个对象提供一个函数。所以这个函数地址是在编译的时候就确定好的。

python 里有两个 decorator：classmethod 和 staticmethod。这两个装饰器起到的作用都是差不多的，都把被装饰的函数变成了 class 的函数，而不是 instance 的函数。区别在于，classmethod 调用的时候会在第一个参数位置传入一个特殊的参数，这个类自己。我们知道 python 是可以把类作为一个参数传进来的。staticmethod则不会传入这个参数。

例子如下：
```python
class Demo:
    @classmethod
    def classmethod(*args):
        return args
    @staticmethod
    def staticmethod(*args):
        return args
Demo.classmethod()
>>> (<class '__main__.Demo'>,)
Demo.classmethod('spam')
>>> (<class '__main__.Demo'>, 'spam')
Demo.staticmethod()
>>> ()
Demo.staticmethod('spam')
>>> ('spam')
```
