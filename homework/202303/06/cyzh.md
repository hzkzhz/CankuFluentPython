### 装饰器

使用方法：

```python
@decorate 
def target(): 
    print('running target()')
    
# 或者：
def target(): 
    print('running target()') 
    
target = decorate(target)
```

装饰器会改变一个函数，比如：

```python
>>> def deco(func): 
...     def inner(): 
...         print('running inner()') 
...     return inner
... 
>>> @deco 
... def target(): 
...     print('running target()') 

>>> target() 
running inner() 
>>> target  
<function deco.<locals>.inner at 0x10063b598>
```

