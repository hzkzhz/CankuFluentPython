# 636~639 Generator - Sentence类3

 - 只要Python函数的定义体中有 yield 关键字，该函数就是生成器函数。调用生成器函数时，会返回一个生成器对象.

 - 生成器可以在每次调用时执行到下一个yield的位置，执行完之后挂起、保存所有状态等待下一次执行。若没有yield可执行则抛出StopIteration异常。
 - 生成器模式的优点是对内存空间的优化。
 - 以下代码输出 0 1 4 9 16
  ```python3
 def gen_sqs():
    for x in range(num):
        yield x ** 2
 for i in gen_squares(5):
    print(i, end=' ')
    
 ```
