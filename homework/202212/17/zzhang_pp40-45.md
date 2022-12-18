# Fluent Python: pp 40-45

#### 2.8.2 用 `bisect.insort` 插入新元素

`insort(seq, item)` 在 seq 里插入item，保持seq升序



### 2.9 当列表不是首选时

不要过度使用列表，存1000万个浮点数用数组array，需要频繁对序列做先进先出操作用deque

#### 2.9.1 数组

- `array.array` 
- 支持 `.pop`, `.insert`, `.extend`
- 支持从文件读取和存入 `.frombytes`, `.tofile`
- 创建需要类型码，`b` 表示一个byte：`floats = array('d', (random() for i in range(10**7)))`

- `array.fromfile` 从一个二进制文件读1000万个float只要0.1秒。
- 相似的序列化替代有：`pickle` 

- 没法就地排序（`list.sort()`），可以用sorted函数新建一个数组 `a = array.array(a.typecode, sorted(a))`.

#### 2.9.2 内存视图 memoryview

- 在不复制内容的情况下操作同一个数组的不同切片

- `memoryview.cast` 可以用不同方式读写同一块内存数据 （可以直接改byte值）

