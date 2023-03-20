# notes

在上一节我们看到一个问题，就是父类如果是一个 builtin type，那么子类重写了一些父类的函数，期待子类的其他继承自父类的函数能够调用子类自己写的函数发现并不能够。

这个问题还体现在其他的类的方法如果调用某个 builtin type 的方法，然后你重写了这个方法，结果并不一定会用你的，因为可能直接从 C 语言层面被拦截了。

所以我们应该 subclass collections.UserDict, collections.UserList，去扩展他们会好很多。

MRO 前面已经讲过了，提前看了一下，很有意思的解决方法。C++的方法是虚继承。

Mixin class 不单独出现，也不是一个具体的类，并不会提供任何具体的功能，它只是增加一些子类的行为。为了实现这样的功能，Mixin class 需要在 MRO 中出现在靠前的位置。这样解析的时候才能用这个函数。