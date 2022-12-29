# 字典和集合

### isinstance()用来检查某个参数是否为 dict 类型，因为这个参数有可能不 是 dict，而是一个比较另类的映射类型。
```
my_dict = {}
isinstance(my_dict, abc.Mapping)
Output: True
```

### 可散列的数据类型
- 可散列对象在整个生命周期中，它的散列值是不变的
- 这个对象需要实现 __hash__(),__eq__() 方法。如果两个可散列对象是相等的，那么它们的 散列值一定是一样的
- 原子不可变数据类型(str、bytes 和数值类型)都是可散列类型，frozenset 也是可散列的
- `TypeError: unhashable type: 'list'`, this is a common error from list when solving algorithm questions.
