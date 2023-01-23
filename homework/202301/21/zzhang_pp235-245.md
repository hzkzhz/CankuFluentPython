# Fluent Python: pp 235-245

10.4.2 slice返回Vector类而不光是list的方法：

- 如果收到的是 `slice` 对象，用`cls` 构造

    ```python
    def __getitem__(self, index):
      cls = type(self)
      if isinstance(index, slice):
        return cls(self._components[index]) # 构造新的Vector实例
      else:
        ...
    # 效果
    # >>> v7[1:4] 
    # Vector([1.0, 2.0, 3.0])
    ```

10.5 动态存取属性比如 实现 `v.x`, `v.y` 读取前两个分量

- 用`__getattr__` 属性，如果实例中没有名为`x`的属性，在`my_obj.__class__` 里也没有等一系列查找都没有的话，就会用`__getattr__` 定义的方法

    ```python
    shortcut_names = 'xyzt'
    def __getattr__(self, name):
    	cls = type(self)
      ...
      pos = cls.shortcut_names.find(name)
      ...
      return self.components[pos] # 省略检查和异常操作
    ```

- 但是这样去 set值 `v.x=10` 会把10绑定到属性`v.x`上，之后访问`v.x`不会再call到`__getattr__`  => 写 `__setattr__` 方法把这种set的方法不合法化

    - 代码略，注意最后要调用超类的处理方法：`super().__setattr__(name, value)`

10.6 散列、快速eq

- 用`functools.reduce` 以及 `operator.xor` 实现 `__hash__`

    ```python
    def __hash__(self):
      hashes = (hash(x) for x in self._components) # 生成器表达式，惰性计算各个分量的散列值
      # hashes = map(hash, self._compoents) # 也是生成器，惰性生成结果
      return functools.reduce(operator.xor, hashes, 0) # 最后的0是初始值
    ```

- 用`all()` 和 `zip` 实现 `__eq__`

    ```python
    def __eq__(self, other):
      return len(self) == len(other) and all(a == b for a,b in zip(self, other))
    ```

    - `zip`函数 返回生成器，坑点：当一个可迭代对象耗尽后，它不发出警告就停止；`itertools.zip_longest` 可以使用可选的`fillvalue` 填充缺失值，直到最长的可迭代对象耗尽

10.7 略 球坐标的实现。
