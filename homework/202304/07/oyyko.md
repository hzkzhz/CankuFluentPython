引入抽象基类之前，Python 就已经非常成功了，即便现在也很少有代码使用抽象基类。第1章就已经讨论了鸭子类型和协议。
接口在动态类型语言中是怎么运作的呢？首先，基本的事实是，，Python 语 言 没 有interface 关键字，而且除了抽象基类，每个类都有接口：类实现或继承的公开属性（方法或数据属性），包括特殊方法，如 __getitem__ 或 __add__。

按照定义，受保护的属性和私有属性不在接口中：即便“受保护的”属性也只是采用命名约定实现的（单个前导下划线）；私有属性可以轻松地访问，原因也是如此。不要违背这些约定。
