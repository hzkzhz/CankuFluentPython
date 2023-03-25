# 865 ~875 python元编程入门-装饰器
 - 感觉最重要的就是利用好装饰器，@decorator这样的形式，执行func等价于decorator(func)，可使用以下带参数的装饰器实现元编程
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

@repeat(3)
def bar():
    print('bar')


if __name__=='__main__':
    foo() # 重复打印默认的2次
    bar() # 重复打印3次
 ```
