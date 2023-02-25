# Fluent Python: pp 740 - 745

## Ch 20 Concurrent Executors

- 主要讲`concurrent.futures.Executor` 这个class
- 之前看过的flags的例子，略
    - `threadpool` 和 `asyncio` 的差不多用1.35-1.4s，而sequential下载的需要7s

- 如果server有很多client发request，而要在coroutine和thread中做选择，选coroutine比较好，因为上下文切换等等会比较省一点。
