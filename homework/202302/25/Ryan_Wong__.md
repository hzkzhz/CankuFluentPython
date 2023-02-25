# 645~660 Generator - 标准库中的Generator1

 - 用于过滤的generator：大多数这类生成器函数接收一个bool断言函数，若为真，则输出相应函数。以下示例均用0~9的list说明
 ```python3
 # compress(it, selector_it), 若selector_it列表里面的为真，则it的对应元素被输出，如果要输出下标为3、5的元素则如下所示
 print([i for i in itertools.compress(range(10), [0, 0, 0, 1,0,1,0])])
 # [3, 5]
 
 # takewhile(predicate, it), predicate是终止条件，如果要输出小于等于5的元素则如下所示
 print([i for i in itertools.takewhile(lambda n: n <= 5, range(10))])
 # [0, 1, 2, 3, 4, 5]
 
 # dropwhile(predicate, it), 是takewhile的反向，满足predicate的直接drop掉，如果要输出大于5的元素则如下所示
 print([i for i in itertools.dropwhile(lambda n: n <= 5, range(10))])
 # [6, 7, 8, 9]
 
 # filter(predicate, it), 很好理解，如果要输出奇数则如下所示
 print([i for i in filter(lambda n: n % 2, range(10))])
 # [1, 3, 5, 7, 9]
 
 # filterfalse(predicate, it), 很好理解，filter的反向，如果要输出奇数则如下所示
 print([i for i in filterfalse(lambda n: n % 2 == 0, range(10))])
 # [1, 3, 5, 7, 9]
 
 # islice(it, stop)或者islice(it, start, stop, ste[=1), 按步长取子序列切片
 print([i for i in itertools.islice(range(10), 2)])
 print([i for i in itertools.islice(range(10), 2, 9, 2)])
 # [0,1]
 # [2,4,6,8]
 
 ```
