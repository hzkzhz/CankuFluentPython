# Fluent Python: pp 335 - 350

14.2

- 迭代器 没法检查是否还有遗留的元素；没法“还原”迭代器

14.3

- 迭代对象只实现`__iter__` 可以多次迭代
- 迭代器实现`__iter__` 和 `__next__`

- 每次调用`iter(my_iterable)` 都新建一个独立的迭代器

14.4

- 生成器的`__iter__` 用`yield` 产生新的element，不用返回东西；不用单独定义一个迭代器类
    - 只要Python 函数的定义体中有`yield` 关键字，该函数就是生成器函数
    - 生成器是迭代器，会生成传给 yield 关键字的表达式的值
    - 生成器函数的定义体执行完毕后，生成器对象会抛出 StopIteration 异常（如果有人for 机制的话，会捕获异常，终止循环没有报错）

14.5  惰性实现

- 用`re.finditer ` 匹配单词，一个个生成单词

    ```python
    import re
    RE_WORD = re.compile('\w+')
    class Sentence:
      ...
      def __iter__(self):
        for match in RE_WORD.finditer(self.text):
          yield match.group()
    ```

    

14.6 生成器表达式

- 列表推导会迫切迭代生成器对象产出的元素 `res1=[x * 3 for x in gen_AB()]`

- 赋值给变量还是一个生成器对象 `res2 = (x*3 for x in gen_AB() ` (生成器表达式)

    - ```python
        def __iter__(self):
        	return (match.group() for match in RE_WORD.finditer(self.text))
        ```

    - 生成器表达式是语法糖:完全可以替换成生成器函数

14.8

- 如果一个类只是为了构建生成 器而去实现` __iter__ `方法，那还不如使用生成器函数

用`itertools` 生成等差数列

- `gen = itertools.takewhile(lambda n: n < 3, itertools.count(1, .5))`
- `list(gen)` => `[1,1.5,2.0, 2.5]`
    - `takewhile` 生成一个使用另一个生成器的生成器，在指 定的条件计算结果为 False 时停止
    - `count(start, step)` 返回的生成器无限生成数字
- 实现生成器时要知道标准库中有什么可用，否则很可能会重 新发明轮子



14.9 标准库中的生成器函数

- 写在下一个Note
