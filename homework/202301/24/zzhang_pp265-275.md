# Fluent Python: pp 265 - 275

11.5 定义抽象基类的子类

- 如果继承`collections.MutableSequence` 必须实现`__delitem`, `insert` 即使不会用到它们
- 可以覆盖从抽象基类继承的方法，自己实现更高效的方法

11.6 标准库中的抽象基类

- 一般在`collections.abc`里，`numbers`和`io` 里也有一些

11.6.1 collections.abc

- 有多重继承
- `Iterable`, `Container`, `Sized` 各个集合应该继承这三个抽象基类
- `Sequence`, `Mapping`, `Set` 有各自`Mutable`的子类
- `MappingView` ：`.items()`, `.keys()`, `.values` 返回的是它的子类的实例
- `Callable`, `Hashable` 主要作用是为内置函 数 isinstance 提供支持
- `Iterator` : `Iterable`的子类

11.6.2 numbers

- `Complex` <- `Real` <- `Rationa` <- `Integral` 
- `decimal.Decimal` 不是 `numbers.Real` ：为了注意Decimal的精度

11.7 定义并使用一个抽象基类（自己最好别写）

- 重点在能读懂抽象基类代码
- 抽象基类：1）继承`abc.ABC`，2）方法加`@abc.abstractmethod`装饰器，3）抽象方法定义体中通常只有文档字符串
- 抽象方法可以有实现代码，但子类必须覆盖抽象方法（可以用`super()`调用抽象方法，为它添加功能）
- 要求某个方法抛出异常，只能在文档中说明
- 子类要实现所有的抽象方法

- 叠装饰器的时候，`abstractmethod`应该在最里层

- 子类可以添加额外的方法
