# Fluent Python: pp 785 - 790

#### The All-or-Nothing Problem

之前的`get_flag` (threadpool)

```python
def get_flag(cc: str) -> bytes:
	url = f'{BASE_URL}/{cc}/{cc}.gif'.lower() 
  resp = httpx.get(url, timeout=6.1,
                   follow_redirects=True)
  resp.raise_for_status()
return resp.content
```

改写成coroutine后的（为了用 async API of HTTPX，只能重写）

```python
async def get_flag(client: AsyncClient, cc: str) -> bytes: 
  url = f'{BASE_URL}/{cc}/{cc}.gif'.lower()
	resp = await client.get(url, timeout=6.1,
                          follow_redirects=True)
return resp.read()
```

- 如果没法把一个blocking function写成coroutine，应该开一个thread/process去跑它

#### Asynchronous Context Managers

- 传统的`with` 不支持coroutine做`__enter__`和`__exit__`
- `async with` 支持，方法名替换成了`__aenter__`和`__aexit__`
    - `__aexit__` coroutine会 await private `__rollback` 或 `__commit`

#### Using asyncio.as_completed and a Thread

- 加上了progress bar 和 error handling

- 用了 semaphore 作为 asynchronous context manager

- 用了`await asyncio.to_thread(save_flag, image, f"{cc}.gif")` 把慢的I/O操作交给另一个thread

    



