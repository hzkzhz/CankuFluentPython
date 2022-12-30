# p0261~0273 Functions as Objects

 - 可以通过别名给函数换名，也能通过map（目前最常用之一的高阶函数）生成函数值的list，例如阶乘函数fact(1)~fact(10)可以这样生成
 ```python3
 list(map(fact, range(1, 10 + 1))
 ```
 - 高阶函数包括map、filter（现在用列表推导代替）、reduce（求和，现在用sum代替）是以函数为参数的内置函数，all和any还在用，前者如果参数里所有可迭代对象为真才返回真，后者如果参数里任意一个可迭代对象为真就返回真
 - python的lambda采用:来分割自变量和因变量。
 - python内置callable可判断一个类的对象是否能作为函数来调用。而用户自定义的类如果要能作为函数的话，需要自己实现__call__
 - python函数内省（introspection）指的是函数专有的属性，除了前面提到的__call__，还有__name__、__closure__、__code__、__defaults__、__globals__等，均可直接print
 - python参数设置捕获较为灵活，*用于捕捉单元素入参，**用于捕捉kv二元类入参（x=y）
