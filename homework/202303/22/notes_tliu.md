# notes

在 missing method 那一节作者介绍了 inconsistent usage of missing method in standard library. 意思就是不同的标准库的类似于字典的数据结构，它的默认行为都不太一样的。也就是说你实现了 missing 之后你可能需要根据你是继承自哪个标准库来决定你需要做哪些额外的事情。

然后我们回到之前的内容 mixin。

我们来看现实世界中的多继承。首先介绍了一下 threadingmixin 用来给 socketserver功能增强成可以多线程处理用的。

然后介绍了在 Django 里面使用 mixin 实现 view 的操作

最后介绍了 tkinter 中的多继承。感觉稍微有点复杂。这几个现实的例子并没有帮到太多，感觉还是要自己写一写才能理解这个事情。

作者认为 GUI toolkit 里继承是非常有用的，这里的类一个继承一个，继承的深度超过四五层都很常见，这个确实是这样，在 C++Qt里面也是如此。

there is still no general theory about inheritance that can guide practicing programmers 

几个有用的 tips：

favor object composition over class inheritance

understand why you use inheritance

make interfaces explicit with ABCs