# notes

什么是 Python 式的代码？没有一个标准的答案。一个例子，如何求和 a[i][1]?

functools.reduce(lambda a, b: a+b, [sub[1] for sub in my_list])

这是一种办法，但是并不好，因为又有 reduce 还有 lambda 还有 list comprehension

去掉 list comprehension 也可以写出来：

functools.reduce(lambda a, b: a + b[1], my_list, 0)

这个比较巧妙，a + b[1]

也可以直接用 numpy：

np.sum(my_array[:, 1])

还有人说：

total = 0
for sub in my_list:
    total += sub[1]

这也是 pythonic。

下一章节我们要讲 interface 借口，protocols 协议，ABC Abstract Base Class。

我们要 program to an interface, not an implementation

面向借口编程，不需要也不应该知道盒子里面是怎么实现的。如果有必要，那就是他的借口抽象的不是很好。

a class is defined by its methods and interfaces.