# notes

学到一个词：on the fly 表示即时的，原地生成。

又学到一个词：coercion 胁迫。大概意思其实和 cpp 里面的运算符类型转化比较像，就是你int + long 会变成 long 这样子。我们可以用 type(self.begin + self.step) 来推断最终的结果的类型是什么。然后用这个类型把我们手上其他的变量的类型也转过去。

作者实现了一个小数 progression 的类，其实就是实现了一个 __iter__ method.

builtin library 也有很多 iter function，非常奇怪的是，有的时候 predicate 在前面，有的时候感觉在后面，并不是很统一的样子。

介绍了 reducing folding accumulating 这三个差不多一个意思。

Haskel 里叫 folding，fold 就是俩俩折叠；reducing 的意思是我们把某个维度给干掉了，这样维度就变少了。accumulate 就是字面意思。