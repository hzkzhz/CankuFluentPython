- list comprehensions
    - for loop to initialize
        ```bash
        >>> symbols = '$¢£¥€¤'
        >>> codes = []
        >>> for symbol in symbols:
        ... codes.append(ord(symbol)) ...
        >>> codes
        [36, 162, 163, 165, 8364, 164]
        ```
    
    - listcomp to build a list
        ```bash
        >>> symbols = '$¢£¥€¤'
        >>> codes = [ord(symbol) for symbol in symbols] 
        >>> codes
        [36, 162, 163, 165, 8364, 164]

        ```

    - Local Scope Within Comprehensions and Generator Expressions. 如果用了listcomp生成list，但是又想像for loop一样保留最后一个variable怎么办？可以用`Walrus operator`
        ```bash
        >>> x = 'ABC'
        >>> codes = [ord(x) for x in x]
        >>> x
        'ABC'
        >>> codes
        [65, 66, 67]
        >>> codes = [last := ord(c) for c in x] 
        >>> last
        67
        >>> c
        Traceback (most recent call last):
            File "<stdin>", line 1, in <module>
        NameError: name 'c' is not defined
        ```

    - listcomp v.s. filter, 可以用if after for 来进行过滤
        ```bash
        >>> symbols = '$¢£¥€¤'
        >>> beyond_ascii = [ord(s) for s in symbols if ord(s) > 127]
        >>> beyond_ascii
        [162, 163, 165, 8364, 164]
        >>> beyond_ascii = list(filter(lambda c: c > 127, map(ord, symbols))) 
        >>> beyond_ascii
        [162, 163, 165, 8364, 164]
        ```
    - Cartesian product
        ```bash
        >>> colors = ['black', 'white']
        >>> sizes = ['S', 'M', 'L']
        >>> tshirts = [(color, size) for color in colors for size in sizes] 
        >>> tshirts
        [('black', 'S'), ('black', 'M'), ('black', 'L'), ('white', 'S'),
        ('white', 'M'), ('white', 'L')] 
        >>> for color in colors:
            ... for size in sizes:
            ...     print((color, size)) 
            ...
        ('black', 'S')
        ('black', 'M')
        ('black', 'L')
        ('white', 'S')
        ('white', 'M')
        ('white', 'L')
        ```