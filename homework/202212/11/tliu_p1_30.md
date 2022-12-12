# Notes1

作者在开头提到, python 是一个比较 consistent 的语言. 它有一些内在的逻辑串联了各个特性. 这使得我们可以非常轻易的理解新特性, 不需要完全推倒重新学一遍.

这一点在 cpp 里可以说是非常传神, cpp11 和之前的 cpp 基本算是两个完全不同的语言, 语法, 机制, best practice 发生了天翻地覆的变化. 这无疑对大家理解产生了障碍.

作者介绍了 `__len__` 方法, 只要实现了这个方法的类型就可以用 len(obj) 的方式获取长度, 有点类似于 duck type, whatever the type is, if it can swim then it is a duck.

在 cpp 里面，vector 我们用 size，但是 string 一般用 length，如果是自己定义的某个类，谁知道会用什么函数名字来代表长度呢？甚至可能是 capacity 之类的东西。所以这是我们用 `__len__` 的一个好处。

在第一个例子里有一个非常有意思的写法：

```py
suits = 'spades hearts clubs diamonds'.split()
```

这样就不需要自己写一个 list，然后自己打空格、打好多引号了。

collection.namedtuple 有点类似 cpp 的没有自己的函数 struct。当我们就是想要把几个变量组合成一个小团体的时候用这个很方便。

当我们实现了 `__len__` 和 `__getitem__` 之后就可以用 random 库的 choice 函数来实现随机挑选一个元素了。

实现 magic method 让外部的库（丰富的标准库、语言特性、第三方库）以一个统一的格式来处理你，非常方便。


