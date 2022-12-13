# p0039~0050 How Special Methods Are Used

 - 特殊方法是连接到python interpreter的桥梁，程序员无需直接调用特殊方法（除了子类调用超类构造器时需要使用__init__），需要记住的是其显式用法，例如list的__iter__()用以下代码代替：
   ```python3
   for x in arr:
   ```
 - 可以通过重写特定的特殊方法来重载运算，例如定义一个二维向量类 class Vector，v1和v2是它的实例，如果不重写__mul__()，v1 * 5 或者v1 * v2只能得到RE。可重写如下：
   ```python3
   class Vector:
       ...
       def __mul__(self, scalar):
           return Vector(self.x * scalar, self.y * scalar) # Vector与数字相乘，v1=(1,2)时v1 * 5 = (5,10)
   ```
   或者
   ```python3
   class Vector:
       ...
       def __mul__(self, rhs):
           return self.x * rhs.x + self.y * rhs.y # Vector内积，v1=(1,2)且v2=(3,4)时v1 * v2 = 11
   ```
 - 特殊方法有较为庞大的列表，书中列举了常用的运算符无关的36个特殊方法和运算符相关的49个特殊方法。
 - len()按理来说应该不同的类各自准备的普通方法，但却被定义为了特殊方法。这是因为取len操作十分常见，而将其定义为特殊方法可使得取len操作直接从C接口读取长度，提升了效率。符合了“practicality beats purity”的论断。
