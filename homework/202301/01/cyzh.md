- 计算阶乘

  ```python
  # 使用reduce函数和一个匿名函数
  from functools import reduce
  def fact(n): 
      return reduce(lambda a, b: a*b, range(1, n+1))
  
  # 使用reduce + operator.mul 函数计算阶乘
  from functools import reduce
  from operator import mul
  def fact(n):
      return reduce(mul, range(1, n+1))
  ```

- `itemgetter`可以用于提取某个字段

  ```python
  cc_name = itemgetter(1, 0) 
  >>> for city in metro_data: 
  ...     print(cc_name(city)) 
  ... 
  ('JP', 'Tokyo') 
  ('IN', 'Delhi NCR') 
  ('MX', 'Mexico City') 
  ('US', 'New York-Newark') 
  ('BR', 'Sao Paulo')
  ```