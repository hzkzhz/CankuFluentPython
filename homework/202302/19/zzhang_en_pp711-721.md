# Fluent Python: pp 711 - 721

Asyncio 和 thread 的区别：

- 如何启动coroutine/thread

    - `asyncio.create_task(...)`的时候返回`Task`，但是其实已经scheduled to run.

    - `Thread` 需要显式地 `spinner.start()` 

- 如何启动另一个coroutine/thread
    - asyncio 会需要 `await slow()` 来显式启动
    - thread的话，就在主线程里像函数调用一样即可

- 如何取消
    - asyncio可以用`Task.cancel()` 方法
    - thread没法直接从外部terminate，需要发送一个信号，比如`Event` 的`done.set()`

- lock、protected
    - Thread需要自己维护lock
    - coroutine 是 protected against interruption的，因为每次只有一个在跑，需要`await` 把control交还给scheduler

### The real impact of the GIL

- 把`time.sleep(3)`或`asyncio.sleep(3)` 改成`is_prime()`之后除了用`process`和`thread`的还有转圈动画，`coroutine`的动画都没了
    - `Thread`的还有是因为每个Thread每5毫秒会被暂停一次，让其他thread试图获取GIL。
    - 解决`asyncio`下的GIL还给别人的问题：让它变成coroutine`async def is_prime(n)`，然后时不时调用`await asyncio.sleep(0)` 把GIL让出去；但这会让程序慢一点

### A Homegrown Process Pool

放到下一个note.

