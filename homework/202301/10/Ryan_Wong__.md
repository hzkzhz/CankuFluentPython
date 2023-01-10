# p0359~0370 Functions as Objects VI - 参数化装饰器

 - 普通装饰器是在已有的function外部套用一层已经写好的功能，比如@lru_cache。而参数化装饰器则是为这层功能添加可控参数，从而在得到更多功能的同时最小化修改。比如说，某个装饰器的功能是重复执行它的入参function，不带参数的装饰器就只能重复固定次数（比如2次），但若将重复次数作为参数即可实现该功能的自由定制。
```python3
def repeat(number=2):
    """多次重复执行装饰函数,
    返回最后一次原始函数调用的值作为结果。
    :param number: 重复次数,默认值是2
    """
    def actual_decorator(function):
        def warpper(*args,**kwargs):
            result = None
            for _ in range(number):
                result = function(*args,**kwargs)
            return result
        return warpper
    return actual_decorator

@repeat()
def foo():
    print('foof')
foo()

@repeat(3)
def bar():
    print('bar')
bar()

```
以上代码执行结果是
```shell
foof
foof
bar
bar
bar
```
