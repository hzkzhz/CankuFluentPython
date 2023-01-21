# Fluent Python: pp 225-235

## Ch 10: 序列的修改、散列和切片

10.2 

- `repr()` 生成字符串在某些情况下会用`...`省略，可以用`reprlib` 展开

10.3 协议和鸭子类型

- 序列协议只需要实现 `__len__` 和 `__getitem__` 两个方法

- 它继承object也没事，说它是序列是因为它的行为像序列 => 鸭子类型

10.4 可切片的序列

- 如果不做任何处理，Vector类的切片返回的是list => 不好

10.4.1

- slice 类型 （内置类型）
    - `S.indices(len) -> (start, stop, stride)` 会把 start、stop 和 stride 都变成非负数，而且都落在指定长度序列的边界内。
    - ` slice(None, 10, 2).indices(5)` => `(0,5,2)` 长度总共5
    - `slice(-3, None, None).indices(5)` => `(2,5,1)` 把起始位置改成正数

