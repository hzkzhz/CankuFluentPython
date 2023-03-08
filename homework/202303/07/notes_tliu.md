# notes

protocol 这里并不是计网里面 TCP HTTP 这些的东西. 而是说如果你希望你的对象是某个类型的, 那么你需要实现哪些东西.

解释器里的这个函数 int PySequence_Check(PyObject *o) 用来判断一个 python 对象是不是 sequence. 判断的方法就是是否支持了 getitem 函数.

作者认为 protocol 像是不正式的 interface. 你可以选择不实现一些方法, 只要你选择实现的这部分能够完成你的要求即可.

用 typing.Protocol 可以让类型检查器要求某个类必须实现某某方法.

Dynamic protocol vs Static protocol
动态协议不要求一定实现, 而且根本没人检查是不是对的
静态协议一定要实现, 有类型检查器来检查是不是对的.