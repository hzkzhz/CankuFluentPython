# notes

with 最经典的用法就是 

with open('xxx') as fp:
    do something

这样的话 fp 会自动关闭。

这里 context manager object 是 with 后面的表达式的最终 evaluation 的值。as 并不是简单把后面的变量绑定到 with 后面的表达式，而是会绑定 with 后面的表示的值的 enter method 的返回值。

as 并不是一个必要的东西，有时候你可以不要 as 只 with。

作者写了一个 mirror module，做了一个 sys output 反向输出的效果，非常有趣。在这个例子里就可以看到 as 得到的结果其实是 enter 方法的返回值。

这个 enter 和 exit 函数都是可以手动调用的，效果上是一样的。