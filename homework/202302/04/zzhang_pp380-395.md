# Fluent Python: pp 380 - 395

Ch 16 协程

16.2

- 就用`x = yield` 从客户那里接受数据
    - 实例化generator后，要先调用`next(...)` 启动协程，才可以调用`send(...)`
- 协程可以身处四个状态中的一个（用`inspect.getgeneratorstate(...)` 确定
    - `GEN_CREATED` 等待开始执行
    - `GEN_RUNNING` 正在执行
    - `GEN_SUSPENDED` 在 `yield` 处暂停
    - `GEN_CLOSED` 结束
-  `b = yield a` 等到客户端代码再 激活协程时才会设定 b 的值！



16.4 预激协程的装饰器

- 每次写成都要 `next()`预激活，容易忘记，可以写个装饰器做这一步

```python
from functools import wraps
def coroutine(func):
	@wraps(func)
  def primer(*args, **kwargs):
    gen = func(*args, **kwargs)
    next(gen)
    return gen
  return primer

# 使用 @coroutine 装饰器
@coroutine
def averager():
  ... 
```

- `yield from` 调用协程时，会自动预激，因此与上面的装饰器不兼容



16.5 终止协程和异常处理

两种方法：

- `generator.throw(...)`
    - 在暂停的yield处抛出制定异常，如果处理了的话，会执行到下一个yield处，产出的值会成为调用 generator.throw 方法 得到的返回值
- `generator.close()`
    - 在暂停的 yield 表达式处抛出 GeneratorExit 异常，如果处理了这个异常或者抛出了StopIteration 异常，调用方不会 报错。
    - 如果收到 GeneratorExit 异常，生成器一定不能产出值，否则解释器会抛出 RuntimeError 异常。



16.6 让协程返回值

- ```python
    def averager():
    	...
    	while True:
        term = yield
    		if term is None:
       		break # 结束
      return Result(..., ...) # 结束的时候才返回值
    
    # catch 这个值的方法
    try:
      coro_avg.send(None) # 结束这个coroutine
    except StopIteration as exc:
      result = exc.value
    # result 里保存了返回的那个value: Result(..., ...)
    ```



16.7 使用 `yield from`

- 主要功能：打开双向通道，把最外层的调用方和最内层的子生成器连接起来，这样二者可以直接发送和产出值，还可以直接传入异常

- （放在下一个note）
