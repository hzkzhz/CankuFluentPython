# Fluent Python (en): pp 813-818

Example 21-16, 21-17 

- 主要是在`python3 -m asyncio`环境下跑了一下*domainlib.py*下的协程

Example 21-18

- 用了一个`loop: Optional[asyncio.AbstractEventLoop]` 避免重复获取 event loop
    - `loop = asyncio.get_running_loop()`

Example 21-19

- 主要调用了21-18 *domainlib.py* 下的异步生成器
    - `async for domain, found in multi_probe(domains): ...`

Generator can be made into context manager

- 用装饰器`@asynccontextmanager`把一个generator变成context manager
    - 和`@contextmanager`装饰器作用差不多
    - before `yield` => `__aenter`
    - after `yield` => `__aexit__`

异步生成器 vs native coroutines

- 都以`async def`声明
- 异步生成器函数体内有`yield`
- 异步生成器只能return empty，native coroutines可以return除了None以外的东西

- naitive coroutine是awaitable的（跟在`await`后面，作为函数参数比如`create_task()`; 异步生成器一般用`async for`来iterate

