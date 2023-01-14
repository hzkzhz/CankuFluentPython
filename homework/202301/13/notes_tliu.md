#notes

函数式语言（比如 Haskell）提供 map，filter，reduce等等高阶函数（也就是接受函数作为参数的函数），在python中也有这种东西，在cpp17中也加入了这些东西。

用 list comprehension 也可以完成类似的事情：

[factorial(n) for n in range(6) if n % 2]

在 python 里创建函数本身就比较简单，lambda 表达式的意义并没有 cpp 里面那么大。在这里 lambda 表达式只能是一个 expression，不能包含如 while try 之类的东西
