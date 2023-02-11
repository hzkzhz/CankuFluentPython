# notes

看了半天, 原来 Strategy pattern 是一种 pattern, Strategy 是它的名字. 这种 pattern 的思路就是把若干种算法都封装好, 客户想用哪个用哪个, 不必知道具体的算法细节. 比如超市要推广, 那么有若干种可能的推广方式. 

在例子里有几点值得注意:

1. 继承 ABC 当作抽象基类
2. 使用 abstractmethod 装饰器修饰虚函数

巧妙使用 list comprehension `return max(promo(order) for promo in promos)`
找到最好的折扣方式.

用 decorator 可以实现一个注册效果, 比如别的什么都不做, 就是把被装饰的函数直接加到 list 里这样子.

command pattern 是说有一个菜单, 上面有若干 command, 然后具体 command 的实现被屏蔽掉. 感觉是个非常无聊的 pattern(?)