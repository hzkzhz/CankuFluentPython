# Fluent Python EN - ch5: data class builder (pp163en - pp199en)

写比较简单的class的三种方法：

1. `collections.namedtuple`
    - tuple 的 subclass
2. `typing.NamedTuple`
    - tuple 的subclass
3. `@dataclasses.dataclass`

用 NamedTuple:

```python
from typing import NamedTuple

class Coordinate(NamedTuple) 
	# Coordinate依旧是 tuple 的 subclass 而不是 typing.NamedTuple 的subclass
  # 用到了 metaclass 
	...
```

用 @dataclass:

```python
from dataclasses import dataclass

@dataclass(frozen=True) # 实例initialized 之后不让 assign value 
class Coordinate:
  # 是 object 的 subclass
  # does not depend on inheritance or a metaclass
  # should not interfere with your own use of these mechanisms
```

取得`__annotations__` 用

- `typing.get_type_hints`
