# 805~827
 - asyncio支持的协程：
    - 使用asyncio启动协程和threading的线程都可以用于并行I/O任务，他们提供了相同的同步原语和都支持安全队列数据结构。
    - 但asyncio（通过把任务委派/注册给asyncio包）可实现多个task/函数的直接切换，且不受GIL控制、提供了非阻塞I/O，实现了面向异步的编程。
 - 适合asyncio的场景
    - 高I/O的爬虫类应用。 示例
    ```python3
    import asyncio


    async def crawl_page(url):
        print('crawling {}'.format(url))
        sleep_time = int(url.split("_")[-1])
        await asyncio.sleep(sleep_time)
        print("OK {}".format(url))

    async def main(urls):
        tasks = [asyncio.create_task(crawl_page(url)) for url in urls]
        for task in tasks:
            await task

    if __name__ == "__main__":
        asyncio.run(main(["url_1", "url_2", "url_3", "url_4"]))

    output :
    crawling url_1
    crawling url_2
    crawling url_3
    crawling url_4
    OK url_1
    OK url_2
    OK url_3
    OK url_4
    ```
