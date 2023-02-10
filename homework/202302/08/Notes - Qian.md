# Static Protocols
```
# Any Iterable type can be used as the first parameter.
def top(series: Iterable[T], length: int) -> list[T]:
    ordered = sorted(series, reverse=True)
    return ordered[:length]
    
top([4, 1, 5, 2, 6, 7, 3], 3) # [7, 6, 5]

l = 'mango pear apple kiwi banana'.split()
top(l, 3)                     # ['pear', 'mango', 'kiwi']
```

### You can wrap Protocol to have a new class
```
from typing import Protocol, Any

class SupportsLessThan(Protocol):
    def __lt__(self, other: Any) -> bool:
        pass
        
from collections.abc import Interable
from typing import TypeVar
from comparable import SupportsLessThan

LT = TypeVar('LT', bound=SupportsLessThan)

def top(series: Iterable[LT], length: int) -> list[LT]:
    ordered = sorted(series, reverse=True)
    return ordered[:length

```

As shown above, SupportsLessThan has `__lt__`. So it enables series sorted using this method.
