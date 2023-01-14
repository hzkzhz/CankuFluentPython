# Fluent Python: pp 193 - 200

8.4.2

- 即使default是None，如果用 `self.passengers = passengers`，其中`passengers` 是传入的list的话，改变`self.passengers` 还是会改变原来的`passengers`，所以要创建副本`self.passengers = list(passengers)`

- 把参数赋值给实例变量之前一定要三思！

8.5 del 和垃圾回收

- `del` 删除名称，而不是对对象。
    - CPython对象的引用归零的时候会被销毁
    - CPython 2.0 用的 分代垃圾回收算法
    - Python还有其他垃圾回收实现，引用数为零时可能不会立即调用`__del__`方法

- `__del__` 不会销毁实例，是即将销毁实例的时候，Python解释器调用`__del__`方法给实例最后的机会释放外部资源

8.6 弱引用

- 弱引用不会增加对象的引用数量 => 不妨碍所指对象 (referent) 被当作垃圾回收
- Python 控制台会自动把 `_` 变量绑定到结果不为 None 的表达式结果上！容易有神奇的bug

8.6.1 `WeakValueDictionary`

- 可变映射：值是对象的弱引用，如果对象被当作垃圾回收后，对应的key也会从`WeakValueDictionary`中自动被删除
- 例8-19有展示了神奇bug：`for cheese in cataglog` 中 `cheese` 临时变量是全局变量，增加了引用
- 相似的还有`WeakKeyDictionary`：键是弱引用

- 相似的还有`WeakSet`：元素没有强引用的时候自动删除这个元素 => 用途：一个类想知道所有实例

8.6.2 弱引用的局限

- 弱引用的目标有局限：list 和 dict实例不行，但他们的子类可以；set实例可以；用户定义的类型可以；int 和 tuple的实例及其子类都不可以

8.7 不可变类型相关

- 元组 t[:], tuple(t) 都返回同一个元组的引用
- str, bytes, frozenset有相似行为（但 frozenset实例不是序列，不能用[:]). fs.copy() 也返回同一个对象的引用
- str 和小的整数 上会有 `interning`驻留优化。
