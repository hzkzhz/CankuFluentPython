- 使用dir函数可以探知函数属性

  得到用户没有但是函数有的属性列表方法

  ```python
  >>> class C: pass
  >>> obj = C()  
  >>> def func(): pass 
  >>> sorted(set(dir(func)) - set(dir(obj))) #获得差值
  ['__annotations__', '__call__', '__closure__', '__code__', '__defaults__', 
  '__get__', '__globals__', '__kwdefaults__', '__name__', '__qualname__']
  ```

  