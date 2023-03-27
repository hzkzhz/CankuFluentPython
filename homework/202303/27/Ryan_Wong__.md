# 909以后 python元编程-元类

 - 元类是类的类，一个类的默认元类是type，也只有继承了type的类才能作为自定义元类。对象是调用类得到的，那么类就是调用元类得到的。
 - 类有三大组成部分：
    - 类名class_name='MyTeacher'
    - 基类们class_bases=(object,)
    - 类的名称空间class_dic，类的名称空间是执行类体代码而得到的
    调用元类时会传入以上几个参数。
 - 自定义元类：可以控制子类的产生过程：
 ```python3
 class Mymeta(type):  # 只有继承类type类才能称之为一个元类，否则就是一个普通自定义类
    pass
    # 自定义动作

class MyTeacher(object,metaclass=Mymeta): # MyTeacher=Mymeta('MyTeacher',(object),{...})
    school = 'john'

    def __init__(self,name,age):
        self.name = name
        self.age = age

    def say(self):
        print('%s says welcome to the zhangsan to learn Python' %self.name)
 ```
