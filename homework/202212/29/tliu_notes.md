# Notes

原来有这么多编码方式。看起来只要知道 utf-8 和 unicode 应该就差不多了。

了解编码感觉基本上没有什么意义，除了有的时候配环境或者是某某终端没有显示某某符号的时候需要一些大致的知识来判断一下具体发生了什么事。

跳过去看 data class builders

如果自己实现了一个 class，C++ 中如果你没有重载等号，那么会编译错误；Python 中如果没有实现 __eq__，那么会调用继承自 object 的函数，尝试去比较 object 的 ID。

namedtuple NamedTuple dataclass 有一些区别，需要区分开

