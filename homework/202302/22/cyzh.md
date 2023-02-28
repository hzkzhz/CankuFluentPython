## 第五章：一等函数

- 一等函数

  - 在运行创建
  - 能赋值给变量或者数据机构中的元素
  - 能作为参数传给函数
  - 能作为函数返回结果

- 样例

  ```python
  In [3]: def f(n): 
     ...:     '''returns n!''' 
     ...:     return 1 if n < 2 else n * f(n - 1) 
     ...:                                                                                                              
  
  In [4]: f(22)                         
  Out[4]: 1124000727777607680000
  
  In [5]: fact = f              
  In [6]: fact(3)                        
  Out[6]: 6
  
  In [7]: map(f, range(12))                 
  Out[7]: <map at 0x7f803565a640>
  
  In [9]: list(map(f, range(12)))                            
  Out[9]: [1, 1, 2, 6, 24, 120, 720, 5040, 40320, 362880, 3628800, 39916800]
  ```

  