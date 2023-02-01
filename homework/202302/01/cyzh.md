- 建立一个`3*3 list`
  
  ```python
  board = [['_'] * 3 for i in range(3)] # 正确用法
  
  weird_board = [['_'] * 3] * 3 #3个指向同一对象
  ```
  
- 给元组赋值 `+=` 的结果

  ```python
  In [1]: t = (1, 2, [3, 4])                                                         
  In [2]: t[2] += [6, 7]                                                        
  ---------------------------------------------------------------------------
  TypeError                                 Traceback (most recent call last)
  <ipython-input-2-821b468f2c67> in <module>
  ----> 1 t[2] += [6, 7]
  
  TypeError: 'tuple' object does not support item assignment
  In [3]: t                                                     
  Out[3]: (1, 2, [3, 4, 6, 7])
      
  In [4]: t[2].extend([1, 2]) # 可以避免异常的出现
  In [5]: t                        
  Out[5]: (1, 2, [3, 4, 6, 7, 1, 2])
  ```

- `sort` 和 `sorted`一个改变原数组，一个新建数组
