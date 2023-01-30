# 0517~0540 Class and Protocols VII - 继承的优缺点1
 - 多重继承：允许一个类有多个父类，该类会继承所有父类里面的方法
 - 多重继承遇到重名方法：在继承列表从左到右找，一旦找到就执行：
 ```python3
 class A:
    def ping(self):
        print('ping:', self)
 class B(A):
    def pong(self):
        print('B-pong:', self)
 class C(A):
    def pong(self):
        print('C-PONG:', self)
 class D(C,B):
 
 # D()的实例d在执行d.pong()时是输出B还是C的pong，全看继承列表是C,B还是B,C
 ```
 - 多重继承在子类没有构造函数时：会在继承列表先深度再广度搜寻祖先构造函数。
