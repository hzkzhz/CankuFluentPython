# 909以后 python元编程-可自定义属性的装饰器
 - 书中例子比较无趣，尝试写一下相关内容的扩展。
 - 使用对type元类的不同层次继承来修改属性
 ```python3
 class Meta(type):
    def __new__(cls, name, bases, dct, **kwargs):
        if name == 'Apple':
            dct.update({
                    'sayHi': lambda: 'Hi I am Apple'
                })
       if name == 'Pear':
            dct.update({
                    'sayHello': lambda: 'Hello this is Pear'
                })
        return super().__new__(cls, name, bases, dct, **kwargs)


class Food(metaclass=Meta):
    pass

class Apple(Food):
    pass

class Pear(Food):
    pass

if __name__=='__main__':
    print(Apple.sayHi())
    print(Pear.sayHello())
    print(Pear.sayHi())
 ```
 
 运行时演示如下：
 ```python3
 Hi I am Apple # Apple拥有一个全新的属性sayHi
 Hello this is Pear # Pear拥有一个全新的属性sayHello
 AttributeError: type object 'Pear' has no attribute 'sayHi' # Pear没有sayHi这个属性，报错
```
