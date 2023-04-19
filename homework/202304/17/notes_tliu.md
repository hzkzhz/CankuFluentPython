# notes

大家都打完了, 我直接跳到 meta programming. 

作者建议大家不要在生产中使用这一章节介绍的功能.

这里有一个重要的 method 是 xxx.mro() . 虽然我们之前已经讲过了 __mro__ 那么为什么还需要这个呢?

mro 下划线只是一个变量, 不带下划线是一个 method. method 可以重载, 真正决定顺序的时候用的是 method. 所以我们可以自己决定顺序.

The Built-In Class Factory