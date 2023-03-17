# notes

MRO: method resolution order. 方法解析顺序。它指明了我们在调用一个函数的时候先找哪个再找哪个。

python 使用过这三种 MRO：

1. 从左到右DFS

```python
class A:
    def method(self):
        print("CommonA")
class B(A):
    pass
class C(A):
    def method(self):
        print("CommonC")
class D(B, C):
    pass

D().method()
```

所谓的深搜的方法就是考虑继承关系：
D 继承 BC，BC 都继承 A。
深搜的时候 D --- B（pass掉了） --- A
最终找到了 A。

但是我们的直觉上来说，C其实是实现了这个函数的，但是用的却是 A 的这个函数，而且 A 还是 C 的父类。

为解决旧式类 MRO 算法存在的问题，Python 2.2 版本推出了新的计算新式类 MRO 的方法，它仍然采用从左至右的深度优先遍历，但是如果遍历中出现重复的类，只保留最后一个。

这样的话只有最后一个 A 被保留，我们的 A 就被 C 给屏蔽了。非常符合我们的直觉。

不过这个方法还是有问题，我们看这个例子：

class X(object):
    pass
class Y(object):
    pass
class A(X,Y):
    pass
class B(Y,X):
    pass
class C(A, B):
    pass

这个例子里，按照上面的方法得到的结果不满足单调性，也就是子类的 MRO 中，父类后面那一串的顺序和父类自己的MRO并不一致。

最终我们有一个复杂的方法：C3 method，形式化的说：

the linearization of C is the sum of C plus the merge of the linearizations of the parents and the list of the parents.

这里 merge的运算方式如下：

    检查第一个列表的头元素（如 L[B] 的头），记作 H。若 H 未出现在 merge 中其它列表的尾部，则将其输出，并将其从所有列表中删除，然后回到步骤 1；否则，取出下一个列表的头部记作 H，继续该步骤。

重复上述步骤，直至列表为空或者不能再找出可以输出的元素。如果是前一种情况，则算法结束；如果是后一种情况，Python 会抛出异常。