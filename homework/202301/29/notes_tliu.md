# notes

blogosphere 博客空间
closure 有时候和匿名函数混为一谈，因为它们有相似的发展缘由，在函数里定义函数并不是很方便，为了解决这样的问题，匿名函数应运而生。closure 在函数嵌套的时候才有意义，所以这两个概念有非常强的关联性。

closure 是一个函数加上一些变量，这些变量既不是全局的也不是局部变量，而是来自外层函数的local scope。

文中给出的第一个例子 avg 是一个 callable 对象的实例，这个对象同时有一些成员变量，看起来像是 cpp 里面的仿函数 functor。

第二个例子

```python
def make_averager():
    series = []

    def averager(new_value):
        series.append(new_value)
        total = sum(series)
        return total / len(series)
    
    return averager
```

这个例子在 cpp 里可以通过外层函数用 static 变量，内部返回一个 lambda 表达式来对应。