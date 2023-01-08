p0341~0358 Functions as Objects V - 闭包与标准库装饰器
 - 闭包可看做是函数嵌套里的内层函数，可引用外层函数定义的变量，该内层函数通常是外层函数的返回值，用以记住内层函数定义时的环境，实现在外层函数的外部访问外层函数的变量（通过闭包保存在内存之中），如以下代码，：
 ```python3
 def f1():
     num = 2
     def f2():
         print(num)
     return f2
 
 action = f1()
 action() # 将会打印num的值2，即使f1已经在上一行结束后退出了
 ```
 - 标准库装饰器之1：@functools.lru_cache，用来一键实现记忆化搜索，无需像cpp那样手动添加缓存结构体。
 - 标准库装饰器之2：@functools.singledispatch，用来实现python本身不支持的重载函数功能。比如根据入参类型重载：
 ```python3
 @functools.singledispatch
 def foo(obj):
     # 函数功能
 
 @foo.register(type1):
 def _(x1):
     # 针对type1的x1的操作
     
 @foo.register(type2):
 def _(x2):
     # 针对type2的x2的操作
 ```
