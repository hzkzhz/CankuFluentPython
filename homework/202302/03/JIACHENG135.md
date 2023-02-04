- Python 何时执行decorator？
    - they run right after the decorated function is defined.
- 变量域的规则

    ```python3
    >>>b=6
    >>> def f2(a):
    ... print(a)
    ... print(b)
    ... b=9
    ...
    >>> f2(3)
    3
    Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    File "<stdin>", line 3, in f2
    UnboundLocalError: local variable 'b' referenced before assignment
    ```

    - python编译这个function的时候，由于在print后面print了b，生成的字节码会去local scope找b，所以会报错

- 关于闭包
    - To summarize: a closure is a function that retains the bindings of the free variables that exist when the function is defined, so that they can be used later when the func‐ tion is invoked and the defining scope is no longer available.
    - `nonlocal` 关键字
        - 能显示的声明free variable，即使在nested function内有对这个变量重新赋值，nonlocal能自动update closure内的变量