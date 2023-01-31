- 学会使用`namedtuple`给字段命名
  
  ```python
  >>> City = namedtuple('City', 'name country population coordinates') #定义一个nt
  >>> tokyo = City('Tokyo', 'JP', 36.933, (35.689722, 139.691667)) #赋值为city类型
  >>> tokyo 
  City(name='Tokyo', country='JP', population=36.933, coordinates=(35.689722, 
  139.691667)) 
  ```
  
- `s[a:b:c]` 的形式对s 在a 和b 之间以c 为间隔取值。c 的值还可以为负

  ```python
  In [1]: s = '123456789'
  In [4]: s[::3]                                             
  Out[4]: '147'
      
  In [5]: s[::-3]                                                     
  Out[5]: '963'
  ```

  

