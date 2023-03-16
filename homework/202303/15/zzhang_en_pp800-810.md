# Fluent Python: pp 800-810

写了一个mojifinder 的server和client

- 用了`unicorn`这个包去跑这个application

- FastAPI 用了asyncio，所以调用FastAPI的接口的时候自动有异步I/O

- 在`supervisor()`里用`await server.serve_forever()` 阻止函数返回。

- 用`StreamWriter.write() ` （非coroutine），发送字符串
- 用`StreamWriter.drain()` （coroutine），flush writer buffer
- 用`StreamReader.readline()` 来（coroutine）读数据（bytes格式）
- `StreamWriter.writelines()`不是coroutine
