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