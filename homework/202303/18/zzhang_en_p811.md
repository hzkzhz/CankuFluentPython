# Fluent Python: p 811

##### Asynchronous Iteration and Asynchronous Iterables

还可以实现异步的iterables (通过实现`__anext__`)

例子（PostgreSQL driver读数据）

- 每次查询返回一行，但在实际情况下，可能有数千行来响应查询。 对于大型响应，cursor不会在单个batch中加载所有行。 因此，重要的是 `async for row in cur`: 不会在cursor可能正在等待其他行时阻塞event loop

```python
async def go():
  pool = await aiopg.create_pool(dsn)
  async with pool.acquire() as conn:
    async with conn.cursor() as cur:
      await cur.execute("SELECT 1")
      ret = []
      async for row in cur: # 重点在这一行
        ret.append(row)
      assert ret == [(1,)]
```

