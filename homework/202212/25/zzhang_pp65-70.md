# Fluent Python: pp 65-70

### 3.5 字典的变种

1. `collections.OrderedDict` Key是ordered的，`popitem()` 删最后一个加进去的，`popitem(last=False)` 删第一个加进去的
2. `collections.ChainMao` 容纳数个不同的映射对象，查询的时候会被当做一个整体逐个查找，直到键被找到为止
3. `collections.Counter` 给每个Key准备整数计数器，`+`/`-` 合并记录，`most_common([n])` 返回最常见的key和计数



### 3.6 子类化 `UserDict`

- 实现之前那个 `StrKeyDict0`的时候用`UserDict`比较好，避免`dict`的捷径实现，导致一些问题（比如无限递归）

- `UserDict` 不是 `dict` 的子类，它继承的是 `MutableMapping`

- 它有一个`data`的属性，是`dict`的实例

  ```python
  class StrKeyDict(collections.UserDict):
    def __missing__(self, key): 
      	if isinstance(key, str):
        		raise KeyError(key)
       	return self[str(key)]
      
    def __contains__(self, key):
    		return str(key) in self.data
      
    def __setitem__(self, key, item): 
      	self.data[str(key)] = item # 注意这里用了 self.data
  
  ```

  相比之前用`dict`的实现，少了`get(...)`



### 3.7 不可变映射类型

- 标准库里是没有这种类型的，但可以自己写

`types` 模块里有一个`MappingProxyType`，返回只读视图，不可修改

```python
from types import MappingProxyType
d = {1: 'A'}
d_proxy = MappingProxyType(d)
d_proxy # mappingproxy({1: 'A'})
d_proxy[1] # 'A'
d_proxy[2] = 'x' # error!
d[2] = 'B' # okay
d_proxy[2] # 'B' 
```

所以可以只暴露 `MappingProxyType` 类型的映射，避免原始映射被不小心修改。



### 3.8 集合论

- 集合中的元素必须可hash，set本身不可 hash，frozenset可以被hash
- 集合实现了中缀运算符 `a | b`, `a & b`, `a - b`
- make things easy `found = len(needles & haystack)` 要求`needles` 和 `haystack` 都是set 类型
- `found = len(set(needles).intersection(haystack))`

#### 3.8.1 集合字面量

- 创建空set: `set()` ，用`{}` 会创建空字典

- 用 `{1,2,3}` 比 `(set([1,2,3]))` 要快，因为用了 `BUILD_SET`的字节码

  

