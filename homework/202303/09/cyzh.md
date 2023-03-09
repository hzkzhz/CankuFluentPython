- 变量作用域

```python
>>> b = 6 
>>> def f2(a): 
...     print(a) 
...     print(b) 
...     b = 9 
... 
>>> f2(3) 
3 
Traceback (most recent call last): 
  File "<stdin>", line 1, in <module> 
  File "<stdin>", line 3, in f2 
UnboundLocalError: local variable 'b' referenced before assignment
```

> 虽然有全局变量b的存在，但是因为函数中有局部变量b，默认使用局部变量b，又print(b)在局部变量b之前，所以会报错，如果要使用全局变量，可以使用global b来定义

