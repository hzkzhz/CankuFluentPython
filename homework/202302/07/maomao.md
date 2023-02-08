本章的主题是对象与对象名称之间的区别。名称不是对象，而是单独的东西。
本章先以一个比喻说明 Python 的变量：变量是标注，而不是盒子。

首先，我们要抛弃变量是存储数据的盒子这一错误观念。
人们经常使用“变量是盒子”这样的比喻，但是这有碍于理解面向对象语言中的引用式变量。Python 变量类似于 Java 中的引用式变量，因此最好把它们理解为附加在对象上的标注。

创建对象之后才会把变量分配给对象.

因为变量只不过是标注，所以无法阻止为对象贴上多个标注。贴的多个标注，就是别名

每个变量都有标识、类型和值。对象一旦创建，它的标识绝不会变；你可以把标识理解为对象在内存中的地址。is 运算符比较两个对象的标识；id() 函数返回对象标识的整数表示。

对象 ID 的真正意义在不同的实现中有所不同。在 CPython 中，id() 返回对象的内存地址，但是在其他 Python 解释器中可能是别的值。关键是，ID 一定是唯一的数值标注，而且在对象的生命周期中绝不会变。
其实，编程中很少使用 id() 函数。标识最常使用 is 运算符检查，而不是直接比较 ID。