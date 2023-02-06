# Fluent Python: pp 425 - 440

17.4 `executor.map`

```python
executor = futures.ThreadPoolExecutor(max_workers=3)
results = executor.map(loiter, range(5))
# results 是一个生成器，所以可以直接display，不会阻塞，但输出results内容的时候就会等loiter返回了再输出
```

- 函数返回结果的顺序与调用开始的顺序一致。如果第一个调用生成结果用时 10 秒，而其他调用只用 1 秒，代码会阻塞 10 秒

tqdm函数

- 画进度条

17.5 修改后的下载flag方法

- 用`as_completed()` 实现非阻塞下载

    ```python
    with futures.ThreadPoolExecutor(max_workers=concur_req) as executor:
      counter = collections.Counter()
      for cc in sorted(cc_list):
        future = executor.submit(download_one, cc, base_url, verbose)
        to_do_map[future] = cc
      done_iter = futures.as_completed(to_do_map) # 一个迭代器，在future运行结束后产出 future
      for future in done_iter:
        try:
          res = future.result() # 不会阻塞，因为as_completed只会返回结束的future
        except ...:
          ...
    ```



17.5.3

- 多线程要更灵活就用`threading`里的组建：`Thread`, `Lock`, `Semaphore`, `queue`。
- CPU密集型 => 多进程，规避GIL => 更灵活就用`multiprocessing`
    - 在进程之间传递数据比较麻烦



好的实践：

- 把 future 存储在一个字典 中，提交 future 时把 future 与相关的信息联系起来;这样，as_completed 迭代器产出 future 后，就可以使用那些信息。（上面例子里的`to_do_map`）



多进程涉及到的书，可以选着读

- Parallel Programming with Python -- Jan Palach 

- Effective Python -- Brett Slatkin
- 不使用线程或毁掉的现代并发方式：七周七并发模型 -- Paul Butcher
    - Seven Concurrency Models in Seven weeks (When Threads Unravel)

好的Talk/文档

- David Beazley -- “Understanding the Python GIL“ www.dabeaz.com/GIL/
- Jesse Noller (multiprocessing包贡献者) -- “Python Threads and the Global Interpreter Lock”



可能好用的库：

- `lelo` ：定义了`@parallel` 装饰器，可以应用到任何函数上，把函数变成非阻塞:调用被装饰的函数时，函数在一个新进程中执行
- `python-parallelize`：提供了一个 parallelize 生成器，能把 `for` 循环分配给多个 CPU 执行。

