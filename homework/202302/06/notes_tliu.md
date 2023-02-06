# notes

我们在之前讲过 decorator 实际上就是把原来的函数当作参数传入一个新的函数，然后再返回的过程。那么我们很自然的想到，decorator 还能接受别的参数吗？

我们的装饰器函数只能接受我们的被装饰函数，然后返回一个函数。但是我们可以通过 decorator factory 接受参数生成一个 decorator，然后再去修饰我们的被修饰函数。

看这个例子：

```python
registry = set()

def register(active=True):

    def decorate(func):
        print('running register' f'(active={active})->decorate({func})') 

        if active:
            registry.add(func) 
        else:
            registry.discard(func)

        print('running f1()')

        return func 

    return decorate

@register(active=False) 
def f1():
    pass

@register() 
def f2():
    print('running f2()')

def f3():
    print('running f3()')
```

在这里我们可以看到 register 其实是一个 decorator factory，我们之前使用装饰器是直接 @xxx，现在我们是 @xxx()，区别就是 xxx 是另一个函数，返回一个我们的装饰器，然后我们再 @ 它。