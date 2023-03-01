# 645~660 Generator - 标准库中的Generator3
 - 合并多个可迭代对象的生成器函数
 ```python3
 # itertools.chain(it1,[it2...it2])
 # 先产出it1中的元素，然后产出it2中的元素，以此类推，无缝连接在一起
 print([i for i in itertools.chain(range(10), range(11, 20), 'hello world')])
 # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 13, 14, 15, 16, 17, 18, 19, 'h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd']
 
 # itertools.chain.from_iterable(it)
 # 功能同itertools.chain 不过传入的参数的结构有所变化   it的结构：it=[iter1,[iter2...itern]]
 print([i for i in itertools.chain.from_iterable([range(10), 'hello'])])
 # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 'h', 'e', 'l', 'l', 'o']
 
 # itertools.product(it1,...itn,repeat=1)
 # 计算笛卡尔积，从输入的各个可迭代对象中获取元素，合并成由N个元素组成的元组，与嵌套的for循环效果一样，repeat指明重复处理多少次输入的可迭代对象
 print([i for i in itertools.product(range(3), 'hello', 'world', repeat=1)])
 # [(0, 'h', 'w'), (0, 'h', 'o'), (0, 'h', 'r'), (0, 'h', 'l'), (0, 'h', 'd'), (0, 'e', 'w'), (0, 'e', 'o'), (0, 'e', 'r'), (0, 'e', 'l'), (0, 'e', 'd'), (0, 'l', 'w'), (0, 'l', 'o'), (0, 'l', 'r'), (0, 'l', 'l'), (0, 'l', 'd'), (0, 'l', 'w'), (0, 'l', 'o'), (0, 'l', 'r'), (0, 'l', 'l'), (0, 'l', 'd'), (0, 'o', 'w'), (0, 'o', 'o'), (0, 'o', 'r'), (0, 'o', 'l'), (0, 'o', 'd'), (1, 'h', 'w'), (1, 'h', 'o'), (1, 'h', 'r'), (1, 'h', 'l'), (1, 'h', 'd'), (1, 'e', 'w'), (1, 'e', 'o'), (1, 'e', 'r'), (1, 'e', 'l'), (1, 'e', 'd'), (1, 'l', 'w'), (1, 'l', 'o'), (1, 'l', 'r'), (1, 'l', 'l'), (1, 'l', 'd'), (1, 'l', 'w'), (1, 'l', 'o'), (1, 'l', 'r'), (1, 'l', 'l'), (1, 'l', 'd'), (1, 'o', 'w'), (1, 'o', 'o'), (1, 'o', 'r'), (1, 'o', 'l'), (1, 'o', 'd'), (2, 'h', 'w'), (2, 'h', 'o'), (2, 'h', 'r'), (2, 'h', 'l'), (2, 'h', 'd'), (2, 'e', 'w'), (2, 'e', 'o'), (2, 'e', 'r'), (2, 'e', 'l'), (2, 'e', 'd'), (2, 'l', 'w'), (2, 'l', 'o'), (2, 'l', 'r'), (2, 'l', 'l'), (2, 'l', 'd'), (2, 'l', 'w'), (2, 'l', 'o'), (2, 'l', 'r'), (2, 'l', 'l'), (2, 'l', 'd'), (2, 'o', 'w'), (2, 'o', 'o'), (2, 'o', 'r'), (2, 'o', 'l'), (2, 'o', 'd')]
 
 # zip(it1,...itn)
 # 并行从输入的各个可迭代对象中获取元素，产出由N个元素组成的元组，只要有一个可迭代对象到了头，迭代就终止
 print([i for i in zip(range(5), 'hello')])
 # [(0, 'h'), (1, 'e'), (2, 'l'), (3, 'l'), (4, 'o')]
 
 # zip_longest(it1,..itn,fillvalue=None)
 # 与zip作用一样，但是终止条件是最长的可迭代对象到头了才终止，其他可迭代对象空缺的值用fillvalue进行补充
 print([i for i in itertools.zip_longest(range(10), 'hello', fillvalue='default')])
 # [(0, 'h'), (1, 'e'), (2, 'l'), (3, 'l'), (4, 'o'), (5, 'default'), (6, 'default'), (7, 'default'), (8, 'default'), (9, 'default')]
 
 ```
