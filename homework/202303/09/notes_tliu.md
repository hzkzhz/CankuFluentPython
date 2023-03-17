# notes

python 的多态看起来很迷惑，我觉得理解多态还是用静态语言比较好，动态语言多态看起来非常弱智。多态仿佛是一个天然、自然的事情，这样可能会影响对静态语言多态的理解。

python 解决多继承，或者说零星继承的方法是使用 super 函数，可以指定你想要的父亲。也可以解决override重载之后想要原来的函数的问题。

class A:
    def p(self):
        print('A')
class B():
    def p(self):
        print('B')
class C(A,B):
    def p(self):
        print('C')
class D(C):
    def p(self):
        print('D')
a = A()
b = B()
c = C()
d = D()

super(C, d).p() 输出 A
理解了这个就差不多了。