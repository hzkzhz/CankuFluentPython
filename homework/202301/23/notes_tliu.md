#notes

a gradual type system 不是必须的, 也只是用来给 language server linter IDE 这些东西用来提供 warning 或者是生成注释之类的用的. 它并不会在运行时进行类型检查, 不然的话运行效率会更差.

很显然, 这个也不会提高效率, 因为它对运行时并没有什么改变.

可以直接用 mypy 运行代码, 这样会提供类型的报错, 要求函数必须指明参数的类型和返回值的类型.

In practice, it’s more useful to consider the set of supported operations as the defin‐
ing characteristic of a type.

什么是变量类型? 类型就是一个变量支持的操作(或者说函数)的集合. 这个想法很自然, 但是很新颖之前没有想过这件事.