- Modern Replacements for map, filter, and reduce
    ```python
    >>> list(map(factorial, range(6))) [1, 1, 2, 6, 24, 120]
    >>> [factorial(n) for n in range(6)] [1, 1, 2, 6, 24, 120]
    >>> list(map(factorial, filter(lambda n: n % 2, range(6)))) [1, 6, 120]
    >>> [factorial(n) for n in range(6) if n % 2]
    [1, 6, 120]
    ```

- Using partial to use a two-argument function where a one-argument callable is required
    ```python
    >>> from operator import mul
    >>> from functools import partial 
    >>> triple = partial(mul, 3)
    >>> triple(7)
    21
    >>> list(map(triple, range(1, 10))) [3, 6, 9, 12, 15, 18, 21, 24, 27]
    ```