- 装饰器在被装饰的函数定义后立即运行，即Python加载模块时。这是因为装饰器在使用时常常是在一个模块中定义，而应用到其他模块的函数上。、

样例：

```python
registry = []  
def register(func): 
    print('running register(%s)' % func)  
    registry.append(func)  
    return func  
 
@register  
def f1():
    print('running f1()')
@register 
def f2(): 
    print('running f2()') 

def f3():  
    print('running f3()') 

def main(): 
    print('running main()') 
    print('registry ->', registry) 
    f1() 
    f2() 
    f3() 
if __name__=='__main__': 
    main() 
```

>  如果导入registration.py模块，而不去运行它，那么它也会输出如下：

```python
>>> import registration 
running register(<function f1 at 0x10063b1e0>) 
running register(<function f2 at 0x10063b268>)
```

