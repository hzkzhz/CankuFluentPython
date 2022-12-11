# Notes1

作者在开头提到, python 是一个比较 consistent 的语言. 它有一些内在的逻辑串联了各个特性. 这使得我们可以非常轻易的理解新特性, 不需要完全推倒重新学一遍.

这一点在 cpp 里可以说是非常传神, cpp11 和之前的 cpp 基本算是两个完全不同的语言, 语法, 机制, best practice 发生了天翻地覆的变化. 这无疑对大家理解产生了障碍.

作者介绍了 `__len__` 方法, 只要实现了这个方法的类型就可以用 len(obj) 的方式获取长度, 有点类似于 duck type, whatever the type is, if it can swim then it is a duck.
