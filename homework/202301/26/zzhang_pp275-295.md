# Fluent Python: pp 275 - 295

11.7.3 Tombola 的虚拟子类

- 可以用`register`装饰器注册抽象基类的*虚拟子类*

    - ```python
        from tombola import Tombola
        
        @Tombola.register # TomboList注册为Tombola的虚拟子类
        class TomboList(list): 
        	...
        ```

    - 可以支持`issubclass`和`isinstance`查验，但不会从抽象基类中继承任何方法或属性

    - 用继承的方法

        ```python
        @Tombola.register
        class TomboList(list):
        	load = list.extend
        ```

    - 用 `TomboList.__mro__` 查看继承关系 （Method Resolution Order）
        - 只会显示`list`和`object`，不会显示 `Tombola`，因为`Tombolist` 没有从`Tombola`中继承任何方法

11.8 子类测试方法 

- `__subclasses__()` 返回直接子类列表，不含虚拟子类
- `_abc_registry` 抽象基类有这个属性，返回抽象类注册的虚拟子类的*弱引用*。

11.9 Python 使用 register方法

- 不用装饰器的话可以这么写：`Sequence.register(tuple)` , 把tuple 注册为Sequence的虚拟子类

11.10

- 有些时候，即便*不*注册，抽象基类也能把一个类识别 为虚拟子类

- 因为有些抽象基类比如`abc.Sized` 实现了`__subclasshook__`，把实现了`__len__`的都认为是自己的虚拟子类
- 自己写的时候最好别写`__subclasshook__` 而是去register

### Ch 12 继承的优缺点

- 主要讨论：子类化内置类型的缺点；多重继承

12.1

- 内置类型 dict 的`__init__` 和 `__update__` 会忽略覆盖的`__setitem__`方法，但`[]`还是会按照新写的`__setitem__`方法来运作
- 所以 不要子类化内置类型（比如 dict, list, str）！
- 用户自己定义的类应该继承collections模块中的类，比如 UserDict、UserList 和 UserString

12.2 多重继承和方法解析顺序

- 菱形继承：B，C继承自A，D继承自B和C。

- Python中可以用`D.__mro__`去查，按这个顺序去找同名方法
    - 如果要指定超类可以用 `C.pong(self)`
    - 和子类声明中列出超类的顺序有关
        - 把D类声明为class D(C, B):，那么D类的`__mro__`属 性就会不一样:先搜索 C 类，再搜索 B 类

- 方法解析顺序使用 C3 算法计算

