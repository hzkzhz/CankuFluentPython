# 645~660 Generator - 标准库中的Generator2

 - 用于映射的generator：大多数这类生成器函数通过传入的可迭代对象和映射函数func获得一个映射后的新的可迭代对象
 ```python3
 # itertools.accumulate(it, [func]), 不输入func则产出可迭代对象it的前缀和；输入对应的func名则产出到每个index的映射值，例如func=min时，输出到每个index的当前最小值
 nums = [5, 4, 2, 8, 7, 6, 3, 0, 9, 1]
 print(list(itertools.accumulate(nums)))
 # 前缀和序列[5, 9, 11, 19, 26, 32, 35, 35, 44, 45]
 nums = [5, 4, 2, 8, 7, 6, 3, 0, 9, 1]
 print(list(itertools.accumulate(nums,min)))
 # 当前最小值序列[5, 4, 2, 2, 2, 2, 2, 0, 0, 0]
 
 # itertools.starmap(func, it), 输出可迭代对象it经过func操作后的等长序列
 print(list(itertools.starmap(operator.mul, enumerate('hello', 1))))
 # 枚举'hello'每个字母并作累乘，['h', 'ee', 'lll', 'llll', 'ooooo']
 print(list(itertools.starmap(pow, [(2, 5), (3, 2), (10, 3)])))
 # 次方操作序列[32, 9, 1000]

 # enumerate(it, start=0)
 print(list(enumerate('hello', 1)))
 # 枚举序列[(1, 'h'), (2, 'e'), (3, 'l'), (4, 'l'), (5, 'o')]
 
 # map(func, it, [it2,...,itN]) 类似starmap，但可以并行处理多个可迭代对象
 print(list(map(str.upper, 'hello')))
 # ['H', 'E', 'L', 'L', 'O']
 
 ```
