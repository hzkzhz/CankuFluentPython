# Fluent Python - EN: pp 695-705

三种执行单元：

- process
    - 进程间通信：pipe, socket, memory mapped files (只能是bytes格式)
    - 真并行 支持preemptive multitasking
- thread
    - 一个进程起的不同线程分享同一个memory space（可以有live Python objects）
    - 真并行 支持preemptive multitasking
- Coroutine
    - classic coroutine: 生成器构建
    - native coroutine: `async def`
    - 假并行 cooperative multitasking. 有blocking code会卡住

GIL相关

- 写在Python/C level的代码可以lauch 一个thread不受GIL影响，但不能改变Python object，但可以到支持`buffer protocol`的memory underlying object，比如`bytearray`, `array.array`, Numpy array
- I/O function 会释放GIL
- CPU intensive的活就开新的process做

Spinner(thread)的例子：

- `time.sleep()` 会 block calling thread 但是释放GIL
- 值得注意的是：`done=Event()`  来coordinate两个thread
