# notes

很神奇 type hints 居然是一种在运行时完全没有用的, 类似于注释一样, 写给 IDE 或者说 language server 看的东西. 而且是原生语法支持. 

我们在一个类里定义 type hints 可以使用 `__annotations__` 来查看所有的 type hints.

在随后的 Object References, Mutability, and Recycling 章节里作者讲了一个没看懂英文的故事.

好像表达的意思是 object 和 name 是不一样的. 这个是可以理解的, 类似于 cpp 里可以有引用这样的别名存在.

第六章是一个重要的章节, 因为 python 对于内存和对象的管理和 cpp 大相径庭, 需要好好学一下