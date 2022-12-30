# 集合推导
- 交集: `s.__and__(z)`
- 反向交集:` s.__rand__(z)`, `s.intersection(it, ...)`
- s和z的交集并且把结果赋值给s: `s.__iand__(z)`, `s.intersection_update(it, ...)`

# 集合类型的其他方法
- Remove e from s if e exists: `s.discard(e)`
- Remove e from s if e exists else raise KeyError exception:`s.remove(e)`

# dict和set的背后
- 1000 万个键的字典里查找 1000 个数，相当于平均每个数差不多三分之一微秒。
- 散列值计算过程中的随机“加盐”

### How to find a value in hashmap/hashset?
- Python 首 先 会 调 用 hash(search_key) 来 计 算 search_key 的散列值，把这个值最低的几位数字当作偏移量，在散列表里查找表元(具 体取几位，得看当前散列表的大小)。
- 若找到的表元是空的，则抛出 KeyError 异常。
- 若不是空的，则表元里会有一对found_key:found_value。这时候Python会检验search_key == found_key 是否为真，如果它们相等的话，就会返回 found_value。
