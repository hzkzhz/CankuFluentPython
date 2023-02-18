# Fluent Python - EN: pp 705 - 710

`multiprocessing.shared_memory`

- 不支持share用户自定义的类
- 允许 ShareableList（a muyable sequence type that can hold a fixed number of items of type int,float, bool, and None, str, bytes up to 10MB per item）

Coroutine 新版

- `async.run(supervisor())` 简历event loop，block到这个函数返回为止

- `async def supervisor()` 定义coroutine

- `spinner = asyncio.create_task(spin(...))` 立即返回 `asyncio.Task`

- `_ = await slow()` block住supervisor，直到slow()返回

- `spinner.cancel()` 会raise CancelledError，在 `spin()` 函数体里会检测这个CancelledError

- 注意要sleep用 `asyncio.sleep(.1)` 这样才不block其他coroutine

- 如果一个coroutine要 delay for doing nothing，使用`asyncio.sleep(DELAY)`

    
