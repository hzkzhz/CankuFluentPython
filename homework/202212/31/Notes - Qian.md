# 集合推导
交集: `s.__and__(z)`
反向交集:` s.__rand__(z)`, `s.intersection(it, ...)`
s和z的交集并且把结果赋值给s: `s.__iand__(z)`, `s.intersection_update(it, ...)`
