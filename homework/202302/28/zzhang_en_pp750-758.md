# Fluent Python: pp 750-758

#### `Future`:

- `concurrent.futures.Future`
    - 当`Executor.submit()` 接受一个callable（schedule to run ），返回一个Future 实例
- `asyncio.Future`
- 他们的instance都表示一个推迟的计算（最终会跑，scheduled to run）
- 都有一个`.done()` 方法告诉你callable执行好了没
- 都有一个`.add_done_callback()`方法当当前callable完成后invoke另一个callback callable
- 都有一个`.result()` 方法返回callable的结果或者异常
    - `concurrency.futures.Future`会block住caller直到有返回值，但可以设置timeout
    - `asyncio.Future.result` 没有timeout，但更希望用户用`await`来获取返回值
- 还有其他获取results的方法，比如`Executor.map()`

两个例子主要就介绍了两种用`concurrent.futures`方法：

- `ThreadPoolExecutor.map` 和`futures.as_completed`

#### Launching Processes with `concurrent.futures`

- 在IO- bound job里，用Processes相比thread没什么优势，而且process setup起来要更多时间

#### Multicore Prime Checker Redux

- 用`executor.map(check, numbers)` 拿返回值，是按照numbers里的顺序的
