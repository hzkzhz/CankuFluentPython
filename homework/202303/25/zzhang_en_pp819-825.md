# Fluent Python: pp 819-825

##### Async Comprehensions and Async Generator Expressions

- 异步生成器expression可以*在任何地方定义*，但是只能在native coroutine或者异步生成器function里*consume*
- 其他异步相关的expression只能在native coroutine或者异步生成器function里consume *定义和consume*

###### Asynchronous comprehensions

- 三种类型的iterate写法

    - ```python
        result = []
        async for i in iter():
          if i % 2:
            result.append(i)
        ```

    - ```python
        result = [i async for i in aiter() if i % 2]
        ```

    - ```python
        result = [await fun() for fun in funcs()] # given a native coroutine fun
        ```

- `await` 可以在`for`或者`async for`前面
- 也可以在`if `后面：`{name for name in names if (await prob(name)).found}` 做了一下判断

##### async beyond asyncio: Curio

- 在Curio里`getaddrinfo`是`socket`的事情，不是event loop的事情
- 在Curio里，coroutine使用`Task`来包装的，`TaskGroup()`来监视和control各个coroutine，用`TaskGroup.spawn`来启动coroutine
    - 用`async for task in group` 来iterate完成的coroutine，类似于asyncio里面的`as_completed(...)`
- `TaskGroup` 支持*structured concurrency*：使一系列异步的任务在一个block里，有相同的entry和exit point
- 支持`UniversalQueue`供不同threads的communicate
- asyncio一个很大的不好的地方就是经常要用到loop object的方法

##### Type Hinting Asynchronous Objects

- 讲return type的，没怎么看懂，总之`AsyncGenerator`没有return type

##### 
