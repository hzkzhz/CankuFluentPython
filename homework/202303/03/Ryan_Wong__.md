# 645~660 Generator - 标准库中的Generator4

 - 把输入的各个元素扩展成多个输出元素的生成器函数
 ```python3
 
# itertools.combinations(it,out_len)  组合 和顺序无关
# 把it产出的out_len个元素组合在一起，然后产出
print([i for i in itertools.combinations('ABC', 2)])  # 原it是'ABC'，长度为3，产出C(3,2)组合的所有元素，共3个
print([i for i in itertools.combinations('ABC', 3)])  # 产出C(3,3)组合的所有元素，共1个
print([i for i in itertools.combinations('ABC', 4)])  # 产出C(3,4)组合的所有元素，共0个
# [('A', 'B'), ('A', 'C'), ('B', 'C')]
# [('A', 'B', 'C')]
# []
 
# itertools.combinations_with_replacement 组合
# 功能同itertools.combinations，但是也包含自己和自己的组合
print([i for i in itertools.combinations_with_replacement('ABC', 2)])
# 
 
# itertools.count(start=0,step=1)
# 从start开始，以step为步长，不断产出数字
for i in itertools.count(1, 2):
    print(i, end=' ')
    if i > 10: break
print()
# 
 
# itertools.permutations(it,out_len=len(list(it)))
# 把it产出的out_len个元素排列在一起  排列  和顺序有关
print([i for i in itertools.permutations('ABC', 2)])
# 
 
# repeat(item,[times])
# 重复不断的产出指定的元素，除非提供times指定次数
print([i for i in itertools.repeat('hello', 10)])
# 
 
# itertools.cycle(it)
# 从it中产出各个元素，存储各个元素的副本，然后按顺序重复不断地产出各个元素
cy = itertools.cycle('ABC')  # 将it首位相连
while True:
    print(next(cy))
# 
 ```
