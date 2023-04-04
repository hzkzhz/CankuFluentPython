# notes

来到 control flow 这一章。

首先介绍了iterable，它就是首先了 iterator的object，它能够用在 for loop，list comprehension，unpacking，construction of collection

实现了一个 Sentence 类，实现了 iter method，那就是 iterable。 真简单啊，比起 cpp 里面复杂的迭代器分类，这个看起来非常友好非常简单。

可以用 iter() 把一个普通函数变成 callable iterable。