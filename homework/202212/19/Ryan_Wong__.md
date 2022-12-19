# p0083~0100 An Array of Sequences Pairt III

 - /+/=和/* /=操作用于拼接序列时，如果序列是可变的如list或特殊的不可变序列str，会原地拼接；如果是其他不可变的如tuple，则会复制一份再拼接。
 - 拼接时，被拼接的序列不允许是不可变套可变的形式，比如下面的tuple套list的拼接会导致歧义：
 ```python3
 (1, 2, [30, 40])
 ```
 - list.sort()和sorted函数的区别：前者会原地排序，后者会新建list对象。
 - 使用list以外的可变序列1----array：只能包含数字但文件读写比list快
 - 使用list以外的可变序列2----memoryview：不复制内容的情况下操作同一个array的某切片
 - 使用list以外的可变序列3----NumPy和SciPy：前者提供高阶的array以及相应的矩阵运算操作，后者在前者基础上提供数值操作和统计接口
 - 使用list以外的可变序列4----deque和其他queue：collection.deque是线程安全的双向队列。此外用的比较多的有大小堆heapq和进程间通信用的multiprocessing
