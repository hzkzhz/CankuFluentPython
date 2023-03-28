# Fluent Python: pp 825 - 831

#### How Async Works and how it doesn't

如何处理CPU占用瓶颈：

- 委托给Python process pool
- 委托为外部task queue
- 用Cython, C之类的重写，最好能够release GIL
- Do nothing，承受损失，但是记录这个决定



Summary

- 只要开始涉及`async def`，就会有more and more 异步的函数，用一些不支持异步的库就会很麻烦

Further (reading list)

- video (30min): https://www.youtube.com/watch?v=F19R_M4Nay4&ab_channel=JetBrains
- *unsync* library: 提供了一个装饰器，根据需要将coroutine、I/O-bound functions和 CPU-bound functions的执行委托给asyncio、threading或multiprocessing。

- video: EuroPython 2019, *Advanced asyncio: Solving Real-world Production Problems*: https://www.youtube.com/watch?v=sW76-pRkZk8&ab_channel=EuroPythonConference

    
