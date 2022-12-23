# Fluent Python: pp 55-60

### 3.1 泛映射类型 Cont.

并不是所有的不可变类型都是可hash的，比如元组本身不可变，但里面的元素可以变。

### 3.3 常见映射方法

三个：

- `dict`, `defaultdict`, `OrderedDict`
- OrderedDict支持`move_to_end(k, [last])` 把key移到末尾，`__reversed__` 倒转

`setdefault(key, default)` 处理找不到的key
