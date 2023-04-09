# 909以后 python元编程 装饰器举例
 ```
 - sample1：@functools.lru_cache or @functools.cache，用来一键实现记忆化搜索，无需像cpp那样设定dp数组再做记忆化。
 - sample2：@functools.singledispatch，用来实现python本身不支持的重载函数功能。比如根据入参类型重载：
 ```python3
 @functools.singledispatch
 def foo(obj):
     # 函数功能
 
 @foo.register(type_1):
 def _(t1):
     # 针对type_1的t1的操作
     
 @foo.register(type_2):
 def _(t2):
     # 针对type_2的x2的操作
 ```
