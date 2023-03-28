# notes

作者介绍了很多运算符，都见过不用记录。

然后介绍了 rich comparison。我以为我们只需要实现大于号，就能够直接得到小于等于，然后再实现小于号就能得到大于等于，进而得到等于和不同于。按照我的理解应该这些符号里面有两个就是够了。因为他们这几个符号按照布尔代数秩是2. python 里 > < >= <= 如果没有实现，fallback 是 raise typerror。

== 如果没有实现 fallback 是 return id(a) == id(b)

!= 如果没有实现 fallback 是 return not (a == b)

记录一个比较优雅 pythonic 的写法：

```python
class Vector:
    def __eq__(self, other):
        return (len(self) == len(other) and all(a == b for a, b in zip(self, other)))
```

