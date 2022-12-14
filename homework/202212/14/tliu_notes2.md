# notes2

我认为最大的收获在于这样一个思想：tuple are not just immutable lists.
有点类似于一个常 struct 变量，c++ 里面也可以定义一个没有类型名的 struct，只创建一个常量对象，实现的效果是类似的。

还学到了一个有趣 python 写法：

```python
a, b = b, a
```

这种奇技淫巧应该烂大街了，但是第一次看到这种东西还是会觉得很有趣。

之前只知道函数传参的时候可以用 *arg 的方式接受一个list，也可以通过 **kwargs 的形式接受一个字典类型的参数传进去，我们其实还可以：

```python
a, b, *c = range(5)
```

这样 c 就会把剩下的元素装到 list 里面。

比如：

```python
def fun(a, b, c, d, *rest):
    return a, b, c, d, rest

fun(*[1, 2], 3, *range(4, 7))
```

在这个写法里， [1, 2] 被 unpacked，range(4, 7) 被 unpacked，然后在接受的时候 abcd 就接收到了 1234，剩下的给了 rest。

pattern matching 是个新东西，需要再仔细看看
