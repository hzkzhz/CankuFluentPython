# Fluent Python: pp 775 - 779

### Ch 21 Aysnchronous Programming

四种形式

- `async def`
- `await`
- `async with`
- `async`

主要的idea：

- 把慢的操作交给一个thread或者process，而不让它block住event loop

推荐的书：

- Using Asyncio in Python -- Caleb Hattingh

一些定义：

- *Naive coroutine*: 由 `async def` 定义的coroutine function （即使 `await` 没有在函数体内被用到）。`await` 不可以在非*naive coroutine* 函数体内的地方用到
- *Classic coroutine*：生成器函数，消费由`my_coro.send(data)`送来的数据（通过`yield`或通过`yield from`委托给别的coroutine）。已经不再被`asyncio`支持
- *Generator-based coroutine*：带有`@types.coroutine`装饰器的生成器函数

- *Asynchronous generator*：由 `async def` 定义的生成器方程，且函数体内用到了`yield`。它返回一个异步的生成器对象（提供`__anext__` 接口）

给了一个例子，异步地去查domain可不可以访问。

- 用了 naitive coroutine objects
- 用`asyncio.get_running_loop()` 来获得event loop

- `loop.getaddrinfo()` 会尝试用socket连接给定的地址，返回一个元组，如果拿到了就是由这个domain，没拿到会有`sockeyy.gaierror` 
- 用`coros = [probe(domain) for domain in domains]` 调用coroutine
- 用`asyncio.as_completed(coros)` 来拿到完成的数据
    - 用`await`那数据（因为已经结束这个coro了，不会被block的）

- 用`asyncio.run` 来开启event loop。通常就是 `main()` 是一个coroutine，然后在程序入口`asyncio.run(main())`
