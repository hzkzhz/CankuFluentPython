- Generator expression
    ```bash
    >>> symbols = '$¢£¥€¤'
    >>> tuple(ord(symbol) for symbol in symbols)
    (36, 162, 163, 165, 8364, 164)
    >>> import array
    >>> array.array('I', (ord(symbol) for symbol in symbols)) array('I', [36, 162, 163, 165, 8364, 164])

    ```
    - 假如genexpr是某function唯一的input则不需要括弧

- tuple 如果保存了引用，如果引用指向的变量改变了对应的tuple也会改变

    ```
    >>> a = (10, 'alpha', [1, 2]) >>> b = (10, 'alpha', [1, 2]) >>>a==b
    True
    >>> b[-1].append(99) >>>a==b
    False
    >>> b
        (10, 'alpha', [1, 2, 99])

    ```

- `tuple` 有时比 `list` 高效的几点原因
    - python编译器在evaulate tuple的时候会一次操作产生字节码，但是evaluate list时会把每一个element视为分隔的常量，然后放到数据栈，然后再build list。潜台词可能是需要更多的指令集？
    - tuple(t) 和 list(t)：一个不copy直接返回t的引用， 一个需要copy
    - tuple由于在生成时，所需内存大小就确定不会改了，所以直接分配内存，但是list需要扩容啥的，未来可能会重新分配内存
    - 并且list在扩容分配内存的时候，需要copy 引用，这会使得宝贵的CPU缓存更低效

    