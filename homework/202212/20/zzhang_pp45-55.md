# Fluent Python pp 45 - 55

#### 2.9.3 Numpy, SciPy

Numpy 数组存成二进制文件

```python
numpy.save('floats-10M', floats)
```

将数组导入到另一个数组里。用了**内存映射**的机制，它让我们在内存不足的情况下仍然可以对数组做切片

```python
floats2 = numpy.load('floats-10M.npy', 'r+')
```



#### 2.9.4 双向队列和其他形式的队列

双向队列 `collections.deque` 

- 线程安全

- 可以快速从两端添加或者删除元素的数据类型

- 适合作为 “最近用到的几个元素”场景，利用 maxlen:

  ```python
  from collections import deque
  dq = deque(range(10), maxlen=10)
  # rotate
  dq.rotate(3) # 右边的元素会被移到最左
  # deque([7, 8, 9, 0, 1, 2, 3, 4, 5, 6], maxlen=10)
  dq.rotate(-4) # 左侧的元素被移到最右
  # deque([1, 2, 3, 4, 5, 6, 7, 8, 9, 0], maxlen=10)
  dq.appendleft(-1) # 左边插入，右边pop出（因为 maxlen）
  # deque([-1, 1, 2, 3, 4, 5, 6, 7, 8, 9], maxlen=10)
  dq.extend([11,22,33]) # 右边插入，左边的pop出
  # deque([3, 4, 5, 6, 7, 8, 9, 11, 22, 33], maxlen=10)
  dq.extendleft([10, 20, 30, 40]) # 会逐个插入dq左边
  # deque([40, 30, 20, 10, 3, 4, 5, 6, 7, 8], maxlen=10)
  ```

- append和popleft都是原子操作，多线程程序中不需要担心资源锁的问题。



## Ch 3 字典和集合

### 3.1 泛映射类型

抽象基类（两个），可以用collections.abc去查

- Mapping
- MutableMapping

```python
my_dict = {}
isinstance(my_dict, abc.Mapping) # True
```

可以hash的数据类型才可以作为 map里的key。

可以hash的数据类型：（要求）

- 生命周期中，hash值不变
- 实现 `__hash__()` 方法
- 有 `__eq__()` 方法（为了能跟其他键做比较）
