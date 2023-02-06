# Fluent Python: pp 410 - 425

Ch 17 使用future处理并发

`concurrent.futures`

- 主要就是`ThreadPoolExecutor` 和 `ProcessPoolExecutor` 类

    ```python
    # workers = min(MAX_WORKERS, len(cc_list)) 线程个数 
    with futures.ThreadPoolExecutor(workers) as executor:
      res = executor.map(download_one, sorted(cc_list))
      # executor.__exit__ 方法会调用 executor.shutdown(wait=True) 方法，它会在所有线程都执行完毕前阻塞线程
    return len(list(res)) # 如果有线程抛出异常，异常会在这里抛出，这与隐式调用 next() 函数从迭代器中获取相应的返回值一样
    ```

- 通常情况下自己不应该创建future，而要让并发框架实例化

- 客户端代码不应该改变 future 的状态，并发框架在 future 表示的延迟计算结束后会改变 future 的状态

    - 不过可以用`.done()` 方法看是否已经执行
    - 有`.add_done_callback()` 方法：有一个参数是callable对象，future运行结束后会调用指定的可调用对象
    - `.result()` 返回可调用对象的结果，或者抛出执行callable对象时候的异常
        - 如果没有结果，`concurrency` 库阻塞（可以有timeout选项）直到有返回；`asyncio` 不支持timeout，获取结果最后使用`yield from`

- `Executor.map` 返回迭代器，迭代器的` __next__ `方法调用各个 future 的 result 方法

用`futures.as_completed` 

- 参数是一个 future 列表，返回值是一个迭代器，在 future 运行结束后产出 future。

    ```python
    def download_many(cc_list):
    	cc_list = cc_list[:5]
      with futures.ThreadPoolExecutor(max_workers=3) as executor:
        to_do = []
        for cc in sorted(cc_list):
          future = executor.submit(download_one, cc) # 排定可调用对象的执行时间，然后返回一个 future
          to_do.append(future)
        results = []
    		for future in futures.as_completed(to_do): # 非阻塞的
          res = future.result()
          results.append(res)
      return len(results)
    ```

    - 使用`concurrent.futures` 库实现的示例受GIL得限制，其实不能并行下载

17.2 阻塞性I/O和GIL

- CPython和PyPy解释器有GIL限制，Jython和IronPython没有

- 所有执行阻塞型 I/O 操作的函数，在等待操作系统返回结果时都会释放 GIL

    - 一个 Python 线程等待网络响应时，阻塞型 I/O 函数会释放 GIL，再运行一个线程

    - `time.sleep()` 函数也会释放 GIL

17.3 使用进程

- 把`ThreadPoolExecutor` 改成`ProcessPoolExecutor` 就能利用可用的CPU核心了
    - `ProcessPoolExecutor` 类中，`max_workers`参数是可选的，一般用`os.cpu_count()`

- 果使用 Python 处理 CPU 密集型工作，应该试试 PyPy
