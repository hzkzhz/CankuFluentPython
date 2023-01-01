# dict

- dict的键必须是可散列的: 如果你实现了一个类的 __eq__ 方法，并且希望它是可散列的，那么它一定要 有个恰当的 __hash__ 方法，保证在 a == b 为真的情况下 hash(a) == hash(b) 也必定为真。
- 字典在内存上的开销巨大: 列表又必须是稀疏的，这导致它在空间上的效率低下。
- dict 的实现是典型的空间换时间:字典类型有着巨大的内存开销，但它们提供了无视数据 量大小的快速访问——只要字典能被装在内存里。
- 键的次序取决于添加顺序: 即便是给key或者value进行了排序，依然不改变这个dict。That means it equals to another dict with the same key+value pairs.
