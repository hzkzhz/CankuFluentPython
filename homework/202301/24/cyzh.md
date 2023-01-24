- Python数据模型的好处：
  - 不需要记住标准操作的格式名词
  - 可以更加方便的使用标准库

- `bool(x)` 的背后是调用`x.__bool__()` 的结果，如果不存在，解释器会尝试调用`x.__len__()`



- 容器序列：`list`,`tuple`,`collections.deque`能存放不同类型的数据
- 扁平序列：`str`,`bytes`,`bytearray`,`memoryview`,`array.array`只能容纳一种类型
- 可变序列：`list`,`bytearray`,`array.array`,`collections.deque`,`memoryview`
- 不可变序列：`tuple`,`str`,`bytes`