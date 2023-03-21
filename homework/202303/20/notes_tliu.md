# notes

之前在知乎上看的关于 MRO 的讲解好像不完全覆盖书上的内容，重新看一下多继承和 method resolution order

```python

class Root:
    def ping(self):
        print("Root ping")
    def pong(self):
        print("Root pong")

class A(Root):
    def ping(self):
        print("A ping")
        super().ping()
    def pong(self):
        print("A pong")
        super().pong()

class B(Root):
    def ping(self):
        print("B ping")
        super().ping()
    def pong(self):
        print("B pong")

class Leaf(A, B):
    def ping(self):
        print(Leaf ping)
        super().ping()

l1 = Leaf()
l1.ping()
>>> Leaf ping
>>> A ping
>>> B ping
>>> Root ping

l1.pong()
>>> A pong
>>> B pong
```
通过这个例子我们发现 l1 ping 会调用所有类的 ping 函数，但是 pong 函数到 B 这里就停下来了，因为 B 没有 super().pong()

所以当我们以 l1 对象执行 A 函数的 super.pong() 的时候，这个 super 找的并不是 A 的 super 而是 l1 的 super。

所以说 super 做的事情就是在 MRO 序列上找下一个人，然后尝试调用它的函数。

当一个函数调用 super 的时候，我们说这是一个 cooperative 方法。

一定要心中记住 python 是动态语言这样的观念，比如一个类A的某个函数调用了 super().some_method() 然后这个类其实没有父类。这其实没关系，因为如果别人继承了这个类，那么这个函数并不是去调用A的父类的函数，而是调用者的MRO序列上的下一个人的函数。