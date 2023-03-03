- `partial`可以把一个两个参数的函数，改编成为一个参数的函数

  ```python
  triple = partial(mul, 3)
  triple(7)
  21
  ```