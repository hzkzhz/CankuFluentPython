# p0407~0422 Class and Protocols II - 符合python风格的对象2

 - python类的私有属性：使用2个前导下划线修饰python类成员属性可将其变为私有，不会被继承覆盖，比如Base类有一个__x，派生类Derive类也有一个__x，那么它们实际上会被分别改写成改写成_Base__x和_Derive__x。
 - __slots__：python类可以动态地在runtime给实例添加属性，而这样会消耗python类里面__dict__资源，使得内存膨胀。而用__slots__定义属性的话就表明该类只能添加给定的属性，节省了runtime的空间消耗，如以下类Student仅允许name和age两个属性：
 ```python3
 class Student:
    __slots__ = ('name', 'age')
 ```
