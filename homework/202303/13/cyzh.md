实现一个简单的装饰器

```python
import time
def clocked(func): 
    def clocked(*argc):
        t0 = time.perf_counter()
        result = func(*args)
        elapsed = time.perf_counter() - t0
        name = func.__name__
        arg_str = ', '.join(repr(arg) for arg in args) 
        print('[%0.8fs] %s(%s) -> %r' % (elapsed, name, arg_str, result)) 
        return result 
    return clocked        
```

使用装饰器：

```python
import time 

from clockdeco import clock 
@clock 
def snooze(seconds): 
    time.sleep(seconds) 
@clock 
def factorial(n): 
    return 1 if n < 2 else n*factorial(n-1) 

if __name__=='__main__': 
    print('*' * 40, 'Calling snooze(.123)') 
    snooze(.123) 
    print('*' * 40, 'Calling factorial(6)') 
    print('6! =', factorial(6))
```

