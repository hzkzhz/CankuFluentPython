# 645~660 Generator - 标准库中的Generator5

 - 用于重新排列元素的生成器函数
 ```python3
 # itertools.groupby(it,key=None)
 # 产出由两个元素组成的元素，形式为(key,group)，其中key是分组标准，group是生成器，用于产出分组里的元素
 strs_list = ['hello', 'world', 'we', 'price', 'the', 'things', 'when', 'we', 'have', 'lost', 'them', '.']
 strs_list.sort(key=len)  # 先排序
 for key, group in itertools.groupby(strs_list, key=len):  # 根据元素的长度进行分组
     print(key, list(group))
 # 1 ['.']
 # 2 ['we', 'we']
 # 3 ['the']
 # 4 ['when', 'have', 'lost', 'them']
 # 5 ['hello', 'world', 'price']
 # 6 ['things']
 
 # reversed(seq)
 # 从后向前，倒序产出seq seq必须是序列，或者是实现了__reversed__的对象
 strs_list = ['hello', 'world', 'we', 'price', 'the', 'things', 'when', 'we', 'have', 'lost', 'them', '.']
 print(list(reversed(strs_list)))
 # ['.', 'them', 'lost', 'have', 'we', 'when', 'things', 'the', 'price', 'we', 'world', 'hello']
 
 # itertools.tee(it,n=2)
 # 产出一个由n个生成器组成的元组，每个生成器用于单独产出输入的可迭代对象中的元素
 g1, g2 = itertools.tee('ABC')
 print(list(g1))
 print(list(g2))
 # ['A', 'B', 'C']
 # ['A', 'B', 'C']

 ```
