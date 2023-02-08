- 对numpy.ndarray 的行和列进行基本操作
  
  ```python
  >>> import numpy 
  >>> a = numpy.arange(12) #直接生成
  >>> a 
  array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9,  10,  11]) 
  >>> type(a) #显式tpye
  <class 'numpy.ndarray'> 
  
  >>> a.shape  #显式形状
  (12,) 
  
  >>> a.shape = 3, 4 #改变性状
  >>> a 
  array([[  0,  1,  2,  3], 
         [  4,  5,  6,  7], 
         [  8,  9, 10, 11]]) 
  
  >>> a[2] #输出第三行
  array([  8,  9,  10,  11]) 
  
  >>> a[2, 1] #输出第三行第二个
  9 
  
  >>> a[:, 1] #输出所有第二个
  array([1, 5, 9])  
  
  >>> a.transpose() # 沿着对角线翻转数组
  array([[  0,  4,  8], 
         [  1,  5,  9], 
         [  2,  6, 10], 
         [  3,  7, 11]])
  ```
  
  
