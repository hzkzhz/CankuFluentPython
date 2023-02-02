# notes

variable lookup logic

分为三种，第一种是 global declaration，第二种是 nonlocal declaration，第三种是在函数内部 assign，则为 local variable，如果 x 被 referenced，但是没有assigned，也不是 parameter，那么 x 会被在外层的函数里查找，没找到就去global，再没找到就去 __builtins__.__dict__ 

库自带的装饰器中比较有用的：@clock，@cache @cache是记忆化搜索在python中实现的要义，需要再深入研究一下