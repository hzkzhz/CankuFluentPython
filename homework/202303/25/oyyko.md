staticmethod 装饰器也会改变方法的调用方式，但是第一个参数不是特殊的值。其实，静态方法就是普通的函数，只是碰巧在类的定义体中，而不是在模块层定义。

classmethod 改变了调用方法的方式，因此类方法的第一个参数是类本身，而不是实例。
classmethod 最常见的用途是定义备选构造方法

classmethod 装饰器非常有用，但是我从未见过不得不用 staticmethod 的情况。如果想定义不需要与类交互的函数，那么在模块中定义就好了。有时，函数虽然从不处理类，但是函数的功能与类紧密相关，因此想把它放在近处。即便如此，在同一模块中的类前面或后面定义函数也就行了。
