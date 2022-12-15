# p0051~0065 An Array of Sequences Pairt I

 - 了解到python的sequence分为 container 类型和flat类型，前者可以容纳不同类型的数据，后者更接近于C++的数列（内存紧凑，只能存放一个类型的数据）。
 - 也可分为可变与不可变类型，前者如list，后者如tuple和str
 - 列表推导：一行初始化list的python式方法，也可以代替lambda表达式。
 ```python3
 codes = [ord(symbol) for symbol in symbols]
 ```
 - 元组拆包在变量初始化里有着广泛运用，除了已知的平行赋值，包括但不限于交换值、占位符（聚焦少数变量）、拆分可迭代对象、用*获取不定数量的参数（见下列代码）等
 ```python3
  a, b, *rest = range(5) # a = 0, b = 1, c = [2,3,4]
  a, b, *rest = range(3) # a = 0, b = 1, c = [2]
  a, b, *rest = range(2) # a = 0, b = 1, c = []
 ```
 - 具名元组：用一行来构建结构体，初始化每个实例也只需一行，如
  ```python3
   from collections import namedtuple
   City = namedtuple('City', 'name country population coordinates') # 初始化了元组的名字以及每个位置的字段名字，变成了类似C++结构体的东西
   tokyo = City('Tokyo', 'JP', 36.933, (35.689722, 139.691667)) 
   print(tokyo) # City(name='Tokyo', country='JP', population=36.933, coordinates=(35.689722,
139.691667))
   print(tokyo.coordinates) # (35.689722, 139.691667)
  ```
