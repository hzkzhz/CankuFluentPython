# notes

dont check whether it is a duck: check whether it quacks like a duck

我们即将学习如何构建一个 python sequence，或者说让我们自己写的类用起来和一个 sequence 别无二致。

说白了就是要提供一个  __len__ 和 __getitem__

我们想要一个 sequence 是因为我们想提供一个变长的 Vector，N dimension Vector。

在例子里用到了 memoryview(xxx).cast(typecode) 非常不俗，很有 c++ 那味。