# Fluent Python: pp 758 - 761

#### Experimenting with `Executor.map`

和中文版一样的例子

- `results = executor.map(func, range(5))`
- results是一个generator，所以display(results) 就显示是一个generator
- 当`enumerate(results)`的时候其实会执行`_f.result()` block到返回为止，所以输出是按顺序的。
- 如果要按照ready时间去输出，无所谓提交的顺序，就可以结合`Executor.submit`和`futures.as_completed`。
    - 而且`Executor.submit` 可以提交不同的callable
    - `futures.as_completed`也可以处理不同的future（由不同的executor提交的，甚至一些是`ThreadPoolExecutor`提交的，一些是`ProcessPoolExecutor`提交的
