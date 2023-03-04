# notes

现在我们想实现一个 hash 使得我们可以装进 set 里面(配合我们的 eq 方法就可以).

直接构造一个 tuple 非常的耗时, 而且在比较的时候也比较耗时. 这里我们可能有非常多的元素, 所以选择用异或. 

这里可以使用 `functools.reduce(lambda a, b: a ^ b, list())`

这个 reduce 操作非常的好用, cpp17 里面也有这个函数 reduce 和 accumulate 差不多一个意思, accumulate 跑的快一点.

我们进一步可以先 hash 然后再异或, 当作整个 vector 的哈希值.