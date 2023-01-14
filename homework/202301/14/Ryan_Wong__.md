# p0383~0392Functions as Objects VII - 使用一等函数实现设计模式-装饰器对策略模式的加强以及命令模式

 - decorator对基于函数的策略模式有以下加强：
    - 不必使用_promo的前缀
    - 可高亮其策略目的，也方便通过注释decorator而取消策略
    - 方便系统内部跨模块调用策略。
 - “Commands are an object-oriented replacement for callbacks.” 意味着命令模式和callback是一体两面。从方便理解的角度来说可以用面向对象的、必须实例化每条命令的命令模式。但从节省资源（？）的角度来说可以使用callable的方法，将命令存储为一系列的函数接口，提供给调用者使用。
