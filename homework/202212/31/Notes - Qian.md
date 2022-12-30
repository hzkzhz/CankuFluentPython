# 集合推导
- 交集: `s.__and__(z)`
- 反向交集:` s.__rand__(z)`, `s.intersection(it, ...)`
- s和z的交集并且把结果赋值给s: `s.__iand__(z)`, `s.intersection_update(it, ...)`

# 集合类型的其他方法
- Remove e from s if e exists: `s.discard(e)`
- Remove e from s if e exists else raise KeyError exception:`s.remove(e)`

# dict和set的背后

