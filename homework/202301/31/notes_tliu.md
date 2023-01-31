# notes

看起来 python 里的函数和 class 里的变量都是类似于 cpp 里面的 static 变量，具体可以看这个例子：

```python
def make_avg():
    lst = []
    def avg():
        lst.append(1)
        print(lst)
    return avg
    

a = make_avg()
a()
a()
b = make_avg()
b()
b()
a()
```

最终显示的结果是：
[1]
[1, 1]
[1]
[1, 1]
[1, 1, 1]

类的情况也类似。类如果不写 self.xxx 而是直接写 xxx，xxx的行为就和 cpp 里面的 static 差不多是一样的。

我们可以通过查看 avg.__code__.co-freevars __closure__, __closure__[0].cell_contents 来查看闭包中的各种信息，比如自由变量，绑定的值是多少等等。

这个例子：

```python
def make_avg():
    count = 0
    total = 0
    
    def avg(x):
        count += 1
        total += x
        return 1
    return avg
```


这里有一个很有趣的事情，count += 1 这样的代码会被 python 认为是 count = count + 1，而这就是一个赋值语句，所以函数会认为 count 是一个 avg 函数的局部变量，而这个变量还没有被定义过，所以会报错。然而我们实际上希望 count 是来自于外层函数 make_avg 的变量。

为了避免这个，我们可以这样写：

```python
nonlocal count, total
```

