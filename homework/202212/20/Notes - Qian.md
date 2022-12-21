# 序列构成的数组
- 可变序列: list、bytearray、array.array、collections.deque 和 memoryview
- 不可变序列: tuple、str 和 bytes
- 容器序列: list、tuple 和 collections.deque 这些序列`能存放不同类型`的数据
- 扁平序列: str、bytes、bytearray、memoryview 和 array.array，这类序列`只能容纳一种类型`
- 列表推导不会再有变量泄漏的问题: e.g. 
Python 2.7.6 (default, Mar 22 2014, 22:59:38)
     [GCC 4.8.2] on linux2
     Type "help", "copyright", "credits" or "license" for more information.
     >>> x = 'my precious'
     >>> dummy = [x for x in 'ABC']
     >>> x
     'C'
