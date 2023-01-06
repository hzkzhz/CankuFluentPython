# p0333~0340 Functions as Objects IV
 - 装饰器是callable对象，可以理解为一个函数，参数是另一个函数，会对该函数进行处理或调换，在不做任何内部修改的情况下增加额外功能。
 - 装饰器在被装饰的函数定义后立即运行
 ```python3
 @decorator
 def func1():
     ...
 ```
 - 全局变量应一律加上global声明
