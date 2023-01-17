#notes

partial function 有点类似于固定了一些参数之后产生的函数。在函数式编程里面这种操作还是比较常见的，算是一个基本操作。在 python 里需要使用 functools partial 来实现。

比如这是一个例子：

```python
from functools import partial
add_3 = partial(add, 3)
assert add_3(7) == 7
list(map(add_3, range(1, 10)))
[4,5,6,7,8,9,10,11,12]
```

这个东西在 cpp 里面好像并没有对应的实现，我能想到的只有重新写一个函数，然后把那个参数固定成某个值。

或者是写一个functor，里面带有一些参数。