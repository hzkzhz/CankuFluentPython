# Python 元编程总结：
 - 装饰器实现参数可控制的元编程：函数func定义处上一行加@decorator，执行func等价于decorator(func)
 - 重写元类（类class设定继承自metaclass=[类名mc]，然后mc必须继承元类type）以控制实例创建，改变其元类魔法函数如__init__、__call__等来控制实例的创建，如实现单例、禁止创建新实例等。
 - 重写元类（类class设定继承自metaclass=[类名mc]，然后mc必须继承元类type）以自定义属性，改写__new__等相关魔法函数。
 - 重写元类（类class设定继承自metaclass=[类名mc]，然后mc必须继承元类type）以控制类属性顺序，使用特殊方法__prepare__。prepare 方法的第一个参数是元类，随后两个参数分别是要构建的类的名称和基类组成的元组，返回值必须是映射（映射使用SortedDict等有序映射结构保存）。元类构建新类时，prepare 方法返回的映射会传给__new__ 方法的最后一个参数，然后再传给 init 方法。__set__被调用的时候会检查参数类型顺序是否符合前述SortedDict保存的映射。
 - 使用重写参数注解实现方法重载
 - 使用@property装饰器吧类的调用变为属性调用，保护类的封装特性（可以通过只给@property而不给@func.setter的方式实现私有属性只读）。
 - 使用@property的@func.setter时遇到的类型检查容易造成多变量的重复冗余代码，可以用一个统一的函数对所有属性统一处理。

 
 
