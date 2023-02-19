# Python使用register的方式
虽然现在可以把 register 当作装饰器使用了，但更常见的做法还是把它当作函数使用
```
# 把内置类型tuple、str、range 和 memoryview 注册为 Sequence 的虚拟子类
Sequence.register(tuple)
Sequence.register(str)
Sequence.register(range)
Sequence.register(memoryview)
```
