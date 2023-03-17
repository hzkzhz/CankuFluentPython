# Fluent Python: pp 790-797

##### Throttling Request with a Semaphore

- Network client的数量要被限制避免太多的concurrent request => 用Semaphore
- `ThreadPoolExecutor`用`max_workers` 来限制
- asyncio的例子用 `asyncio.Semaphore` 

Example 21.7里：

- 没法按照 future -> country code 的方法map，因为 asyncio.as_completed 返回的awaitable和穿进去的是一样的。？

##### Python's Semaphores

- Python里有三个Semaphore class
    - threading
    - multiprocessing
    - asyncio
        - 当我们`await` 一个`.acquire()` 的协程的时候递减
        - 当我们`.release()`的时候增加

- 例子里把semaphore作为一个context manager，更安全一点
    - `Semaphore.__aenter__` 就是 await for `.acquire()`
    - `Semaphore.__axit__` 就是 call `.release()`

##### Making Multiple Requests for Each Download

- 例子：要下载旗子的图片 + 名字（在metadata.json）里，需要发两个request。=> 需要nested functions（旗子的文件和country code、名字一直在你的closure里直到你可以保存文件为止）

- 给得例子里就是再 await一个 get country 的request

    ```python
    ...
    try:
    	async with semaphore:
        image = await get_flag(client, base_url, cc)
      async with semaphore:
        country = await get_country(client, base_url, cc)
    except ...:
      ...
    ```

- 可以用`asyncio.gather`让`get_flag`和`get_country` 并行地跑。

