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
