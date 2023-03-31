# notes

学到了一个新的名词：augmented assignment 表示 += *= 这样的操作。

需要实现的method是正常的method名字加上一个 i
比如 += 就是 iadd

总结一下，运算符重载只能重载已有的运算符，不能自己创造一个，这是很自然的，不然前端就炸裂了。有一些运算符不能重载，比如 is and or not。单目运算符也可以重载，比如 neg pos 分别代表一个元素前面的 +- 号。

在 add 的时候，如果发现类型不对，不要跑出一场，而是返回 notImplemented，这样可以让python接下来去尝试用 radd 来看看类型是否正确。如果直接抛出异常，那么这个故事就直接停下来了。

判断一个东西是不是一个类型，可以用 ducktype 直接莽，调用你想调用的方法，然后 catch typeerror 异常。或者是使用 isinstance 方法。ducktype比较灵活，isinstance比较可预测。