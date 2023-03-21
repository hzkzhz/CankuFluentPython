# 805~827
 - asyncio支持的协程：
    - 使用asyncio启动协程和threading的线程都可以用于并行I/O任务，他们提供了相同的同步原语和都支持安全队列数据结构。
    - 但asyncio（通过把任务委派/注册给asyncio包）可实现多个task/函数的直接切换，且不受GIL控制、提供了非阻塞I/O，实现了面向异步的编程。
 - 适合asyncio的场景
    - 高I/O的爬虫类应用。 示例
    ```python3
    import asyncio

    async def crawling(time_consumed):
        print('Starting task {}'.format(time_consumed))
        await asyncio.sleep(int(time_consumed[:-1].split("_")[-1])) # 模拟该次爬取所需的时间
        print("Ended task {}".format(time_consumed))

    async def func(urls):
        tasks = [asyncio.create_task(crawling(x)) for x in urls]
        for task in tasks:
            await task

    if __name__ == "__main__":
        print("Before: {}".format(int(time.time())))
        asyncio.run(func(["time_1s", "time_2s", "time_3s", "time_4s"]))
        print("After: {}".format(int(time.time())))

    output : (可以看到只用了4s，说明4个爬虫任务并行执行了)
    Before: 1679418413
    Starting task time_1s
    Starting task time_2s
    Starting task time_3s
    Starting task time_4s
    Ended task time_1s
    Ended task time_2s
    Ended task time_3s
    Ended task time_4s
    After: 1679418417
    ```
