# Tombola子类的测试方法

__subclasses__(): 这个方法返回类的直接子类列表，不含虚拟子类。

_abc_registry: 只有抽象基类有这个数据属性，其值是一个 WeakSet 对象，即抽象类注册的虚拟子类的弱引用。

<img width="698" alt="Screen Shot 2023-02-17 at 11 48 38 PM" src="https://user-images.githubusercontent.com/73077953/219848609-c557bb78-2510-40f5-bb80-fc50985d43ff.png">
