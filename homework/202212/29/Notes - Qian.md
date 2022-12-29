# 字典推导
### If possible, use defaultdict instead of dict. OrderedDict misses some library methds such as `d.__copy__()`
- d.setdefault(k, [default])

### OrderedDict
-Due to the character of ordered, it has some special methods:
`d.move_to_end(k, [last])`, `d.__reversed__()`
 - my_odict. popitem(last=False) 删除并返回第一个被添加进去的元素。

### collections.Counter
`counter.update('aaaaazzz')` => the Counter gets more characters and update the freqency.
`counter.most_common(2)` => get the top 2 frequently key+value

### UserDict
UserDict 有一个叫作 data 的属性，是 dict 的实例，这个属性实际上是 UserDict 最终存储数据的地方。这样做 的好处是，比起示例 3-7，UserDict 的子类就能在实现 __setitem__ 的时候避免不必要的递 归，也可以让 __contains__ 里的代码更简洁。
```
def __setitem__(self, key, item): 
  self.data[str(key)] = item 
```
