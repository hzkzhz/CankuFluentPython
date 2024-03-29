is 运算符比 == 速度快，因为它不能重载，所以 Python 不用寻找并调用特殊方法，而是直接比较两个整数 ID。而 a == b 是语法糖，等同于 a.__eq__(b)。继承自 object 的 __eq__方法比较两个对象的 ID，结果与 is 一样。但是多数内置类型使用更有意义的方式覆盖了__eq__ 方法，会考虑对象属性的值。相等性测试可能涉及大量处理工作，例如，比较大型集合或嵌套层级深的结构时。

元组与多数 Python 集合（列表、字典、集，等等）一样，保存的是对象的引用。如果引用的元素是可变的，即便元组本身不可变，元素依然可变。也就是说，元组的不可变性其实是指 tuple 数据结构的物理内容（即保存的引用）不可变，与引用的对象无关。