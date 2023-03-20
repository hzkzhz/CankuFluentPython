# notes

protocol duck typing 感觉有点无聊，跳到下一章学习一下 inheritance。

继承是一个复杂的问题。首先继承在语义上有歧义。有人用继承来表达：A 继承 B，则 A 是 B 这个语义。比如 A 是猫类，B 是动物类，猫是动物。

也有人用继承来表达某个类需要某个接口，这个就和“猫是动物”这种语义没有任何关系。

C++ 里没有 interface 这种东西（不像java），实现mixin语义需要用到CRTP。

Python 和 C++ 一样都有多继承，好奇 Python 是如何解决多继承里变量的重复、查询之类的问题的呢？尤其是作为一个动态语言。

继承被很多人诟病，认为其实很多时候都不应该使用继承。这个有一定的道理。很多时候我们继承都并不是原本的语义，而是第二种语义。可能可以用更好的词/语法来刻画它。