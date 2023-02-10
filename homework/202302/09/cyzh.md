- 字典的多种创建方式
  
  ```python
  >>> a = dict(one=1, two=2, three=3) 
  >>> b = {'one': 1, 'two': 2, 'three': 3} 
  >>> c = dict(zip(['one', 'two', 'three'], [1, 2, 3])) 
  >>> d = dict([('two', 2), ('one', 1), ('three', 3)]) 
  >>> e = dict({'three': 3, 'one': 1, 'two': 2}) 
  
  >>> a == b == c == d == e 
  True
  ```
  
- `d.values()`返回字典里所有的**值**

- `d.key()`返回字典里所有的**键**
