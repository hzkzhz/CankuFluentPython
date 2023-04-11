# notes

感觉这本书得多看几遍，这个时候提到第九章的例子说实话有一点点迷糊了。

作者介绍了很久 coroutine classic 和 native，但是我根本连什么是 coroutine 都不知道。

实现了一个例子来求平均数，大概就是每次用 yield 来 suspend 一个 coroutine，等待下一个 coroutine.send(xx) 把值给 send 进来继续执行剩下的步骤，然后进入下一个循环。

这个过程看起来是非常异步的。

开启一个 coroutine 使用 next(coroutine) 的方式，关闭一个 coroutine 使用 coroutine.close() 的方式。