# Fluent Python: pp 780 - 785

#### Awaitable

- *native coroutine object* 由调用 native coroutine function得到

- *asyncio.Task* 由 `asyncio.create_task()` 获得

    - 如果不需要返回值或者cancel它，就不用保留这个Task object，让这个coroutine它自己跑就可以了

    - 如果需要返回值才能继续，用`await func_coro()`

 底层实现awaitable的时候需要实现的method

- `__await__` 返回iterator
- `tp_as_async.am_await` （用其他语言写的object）

例子21.2 和 21.3

- `asyncio.gather(*to_do)` 其中`to_do` 是个包含coroutine的list 。`asyncio.gather` 会等所有的awaitable完成返回结果
- 真正做HTTP request的是 `get_flag(...)`
    - 其中`resp = await client.get(...)` 然后返回的是 `resp.read()` Network I/O 也是用的coroutine method
- `save_flag` 本来也应该用async，但是asyncio不支持asyncronous filesystem，之后会把它委托为一个thread去做

The Secret of Naive Coroutines: Humble Generators

- Async 底层是需要`.send()`, `yield`的，但是用了asyncronous库比如 HTTPX之后就不用调用那么底层的API，只需要await, async def就可以了
- `await` 基本上用了 `yield from` 的idea
- `await` 唤醒下一个coroutine

- 用`asyncio.gather`和`asyncio.create_task` 可以有多个同时的`await` channel（多个IO operation，单个event loop，单个thread）



