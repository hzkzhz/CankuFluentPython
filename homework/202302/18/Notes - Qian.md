# Python使用register的方式
虽然现在可以把 register 当作装饰器使用了，但更常见的做法还是把它当作函数使用
```
# 把内置类型tuple、str、range 和 memoryview 注册为 Sequence 的虚拟子类
Sequence.register(tuple)
Sequence.register(str)
Sequence.register(range)
Sequence.register(memoryview)
```

# 即便不注册，抽象基类也能把一个类识别为虚拟子类。

<img width="806" alt="Screen Shot 2023-02-18 at 10 32 40 PM" src="https://user-images.githubusercontent.com/73077953/219932911-12d3bed6-2084-4c69-b5f5-5770b6080f63.png">
