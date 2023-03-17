# Fluent Python: pp 797 - 800

##### Delegating Tasks to Executors

- Python 默认的reading 和 writing并不是异步的，会block event loop

可以用(Python 3.9 +)

```python
await asyncio.to_thread(save_flag, image, f"{cc}.gif")
```

也可以用(Python 3.7 or 3.8)

```python
loop = asyncio.get_running_loop()
loop.run_in_executor(None, save_flag, image, f"{cc}.gif")
```

- 这里None是指用默认的 `ThreadPoolExecutor`
- 如果函数有keyword arguments，那需要用`functool.partial`去实现

不过Davis发现，用线程池在database driver 的一些用例中性能更高（不过一般觉得异步的会比thread的快）

一些用`run_in_executor`的警告

- 处理cancellation的时候会有很难debug的问题，因为thread没有cancellation机制，asyncio.run可能会无限等待一个executor（这个executor自己不会stop）

##### Writing asyncio servers

###### Meet the inverted index

- 把word map到document的位置

- 还有`InvertedIndex.search `功能
