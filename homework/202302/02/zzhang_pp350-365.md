# Fluent Python: pp 350 - 365

14.9 标准库中的生成器函数

1. 过滤 六个
    - `itertools.compress(it, selector_it)`, `itertools.dropwhile(predicate, it)`, `filter(predicate, it)`, `itertools.filterfalse(predicate, it)`, `itertools.islice(it, stop)`, `itertools.takewhile(predicate, it)`

2. 映射 四个

    - `itertools.accumulate(it, [func])`, `enumerate(iterable, start=0)`, `map(func, it1, [it2, ..., itN])`, `itertools.starmap(func, it)`

    - 例子：`list(itertools.starmap(operator.mul, enumerate('albatroz', 1)))` 输出`['a', 'll', 'bbb', 'aaaa', 'ttttt', 'rrrrrr', 'ooooooo', 'zzzzzzzz']`

    - 例子2计算平均值：

        ```python
        sample = [5, 4, 2, 8, 7, 6, 3, 0, 9, 1]
        list(itertools.starmap(lambda a, b: b/a, enumerate(itertools.accumulate(sample), 1))) 
        # [5.0, 4.5, 3.6666666666666665, 4.75, 5.2, 5.333333333333333, 5.0, 4.375, 4.888888888888889, 4.5]
        ```

3. 合并 五个
    - `itertools.chain(it1, ..., itN)`, `itertools.from_iterable(it)`, `itertools.product(it1, ..., itN, repeat=1)`, `zip(it1, ..., itN)`, `itertools.zip_longest(it1, ..., itN, fillvalue=None)`
4. 把输入的各个元素扩展成多个输出元素
    - `itertools.combinations(it, out_len)` （组合，不含重复元素），`itertools.combinations_with_replacement(it, out_len)`, `itertools.count(start=0, step=1)`, `itertools.cycle(it)`, `itertools.permutations(it, out_len=None)`, `itertools.repeat(item, [times])`
5. 重新排序
    - `itertools.groupby(it, key=None)` : 例子： `itertools.groupby(animals, key=len)` 按长度来分组
    - `reversed(seq)` 生成器函数
    - `itertools.tee(it, n=2)` 相当于复制了一下生成器

14.10 `yield from` 

```python
def chain(*iterables):
  for i in iterables:
    yield from i # 不只是替换 for i in it: yield it 一重循环
```

14.11 可迭代的归约函数

- `all(it)`, `any(it)`, `max(it, [key=,][default=])` (如果可迭代的对象为空，返回 default), `min(it, [key=,][default=])`, `functools.reduce(func, it, [initial])`, `sum(it, start=0) `（用`math.fsum` 提高精度）

- `sorted` 返回真正的列表

14.12 `iter` 函数

- `iter(iterable, 哨值)` 当可调用的对象返回这个值时， 触发迭代器抛出 StopIteration 异常，而不产出哨符

    - 例子：逐行读取文件，直到遇到空行或者到达文件末尾为止

        ```python
        with open('mydata.txt') as fp:
          for line in iter(fp.readline, '\n'):
            process_line(line)
        ```

14.14 

- 把生成器当成协程：和`.send()` 有关 允许使用生成器的客户把数据发给自己

拓展：

- yield 关键字只能把**最近**的外层函数变成生成器函数， yield from句法允许生成器或协程把工作委托给第三方完成

    ```python
    def f():
      def do_yield(n):
        yield n
      x = 0
      while True:
        x += 1
        do_yield(x) # wrong!!! 会无限循环
        yield from do_yield(x) # ok!
    ```

    
