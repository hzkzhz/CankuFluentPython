```
from functools import reduce
from operator import add

reduce(add, range(100)) # 4950
```

# Anonymous Functions - lambda
```
fruits = ['strawberry', 'fig', 'apple', 'cherry', 'raspberry', 'banana']
sorted(fruits, key=lambda word: word[::-1]) # sort by the reversed word
```

# User-Defined Callable Types
A class implementing __call__ is an easy way to create function-like objects that have some internal state that must be kept across invocations
