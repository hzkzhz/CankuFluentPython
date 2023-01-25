[toc]

# 装13词汇
## dunder method
magic method == dunder method

"比如 obj[key] 的背后就是 __getitem__ 方法." 读作 "比如 obj[key] 的背后就是 dunder getitem 方法."
## why len is not a method
"practicality beats purity" 读作 "实用胜过纯粹". No method is called for the built-in objects of CPython: the length is simply read from a field in a C struct

# chap01

> 迭代通常是隐式的，譬如说一个集合类型没有实现 __contains__ 方法，那么 in 运算符就
会按顺序做一次迭代搜索。

> 首先明确一点，特殊方法的存在是为了被 Python 解释器调用的，你自己并不需要调用它
们。
 
> 很多时候，特殊方法的调用是隐式的，比如 for i in x: 这个语句，背后其实用的是 iter(x)，而这个函数的背后则是 x.__iter__() 方法。

妙语连珠: 写python,越短越好
> 通过内置的函数（例如 len、 iter、 str，等等）来使用特殊方法是最好的选择. 这些内置
函数不仅会调用特殊方法，通常还提供额外的好处，而且对于内置的类来说，它们的速度 更快。
 
> Python 有一个内置的函数叫 repr，它能把一个对象用字符串的形式表达出来以便辨认，这
就是“字符串表示形式”。__repr__ 和 __str__ 的区别在于，后者是在 str() 函数被使用，或是在用 print 函数打印 一个对象的时候才被调用的，并且它返回的字符串对终端用户更友好。 