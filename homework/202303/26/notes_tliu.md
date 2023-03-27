# notes

最简单的 overload 就是重载加法。在 cpp 里面大家也经常重载这种基本运算，比如给矩阵之类的东西重载加号。

在这里我们可以给这本书之前实现的 vector 类重载一下加号，实现一个 add method 

非常有意思的是 a + b 可以理解为 a.add(b) 也可以理解为 b.radd(a)

显然，首先应该被理解为 a.add(b) 更合理。如果 a 并没有实现 add ，那么python会尝试去找 b.radd() 。这是一个很有趣的区别，C++里面一定是 a.add(b) 找不到就 compile error。

python 里还能重载 @ 运算符。在 julia 里面 @ 是一种类似于装饰器一样的东西，在 python 里这就是一个运算，被用在矩阵乘法上。我们要重载这个函数也是去重载 __matmul__ 这个 method。