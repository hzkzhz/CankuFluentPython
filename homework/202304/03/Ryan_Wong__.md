# 909以后 python元编程-property装饰器
 - 为了保护类的封装特性，把类的调用装饰为属性的调用，即Foo.func()变成了Foo.func，以可读形式对外提供（可看做是@func.getter）。
 - 可以用@func.setter为对应属性提供修改功能
 - 可以用@func.deleter为对应属性提供删除功能
 ```python3
 class Rect:
    def __init__(self, area):
        self.__area = area
        
    @property
    def area(self):
        return self.__area
    
    @area.setter
    def area(self, value):
        self.__area = value
        
    @area.deleter
    def area(self):
        self.__area = 0
        

# 运行
rect = Rect(80)
print("矩形的面积是：", rect.area)
rect.area = 30
print("修改后的面积：",rect.area)
del rect.area
print("删除后的area值为：",rect.area)
# 矩形的面积是： 80
# 修改后的面积： 30
# 删除后的area值为： 0
 ```
