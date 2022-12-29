# 不可变映射类型
`MappingProxyType`是个只读视图, 只有原来的映射发生变化，它才会发生变化。
```
from types import MappingProxyType
d = {1:'A'}
d_proxy = MappingProxyType(d)
print(d_proxy[1]) # Output: 'A'

d_proxy[2] = 'x' # Cause error when assigning a new value.
d[2] = 'B' # Make change on the original dict.
print(d_proxy[2]) # Output: 'B'
```
# frozenset
- set 类型本身是不可散列的，但是 frozenset 可以。因此 可以创建一个包含不同 frozenset 的 set。
- Freeze the list, and make it unchangeable.
```
mylist = ['apple', 'banana', 'cherry']
x = frozenset(mylist)
x[1] = "strawberry" # This would cause error since x is unchangable.
x.add("pear") # This would cause error since x doesn't have attribute 'add'
```
