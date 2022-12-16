# Fluent Python: pp 31-40

### 2.4.4

- `l[2:5]=100` 错误，左边是切片，右边必须是一个可迭代的值
- `l[2:5]=[100]` 三个数变成一个数100



## 2.5 对序列用 + 和 *

- `[1,2,3]*3`, `5*'abc'` 都可以
- `my_list=[[]]*3` 来初始化一个列表组成的列表，3个元素其实是3个引用，指向的都是同一个列表

```python
board=[['_'] * 3 for i in rang(3)] # ok

board=[['_'] * 3] * 3 # not ok

row = ['_'] * 3
board = []
for i in rang(3):
  board.append(row) # not ok
 
board = []
for i in rang(3):
  row = ['_'] * 3
  board.append(row) # ok
```



## 2.6 +=, *=

- `__iadd__`, `__imul__` 原地加/乘
- 没实现就会新建一个对象再赋值

 神奇的例子

```python
t = (1, 2, [30, 40])
t[2] += [50, 60]
# 既真的改变了元组，又跑出了 tuple 不支持assignment的异常
# 因为Python实现这个赋值的时候会1）先取这个元组的值，2）原地加之后，3）assign回元组的时候抛出异常
```

- 不要把可变对象如list 放在元组中
- 增量赋值不是一个原子操作。有异常还是加了
- 学会看Python的字节码



## 2.7 `list.sort`, `sorted`

- `list.sort` 原地sort，返回None
- `sorted` 会返回一个新建的列表

参数：

- reverse: True/False
- key: e.g., key = str.lower, key = len



## 2.8 用 `bisect` 来管理已排序饿序列

- `bisect`, `insort`

- 先用 `bisect(haystack, needle)` 查找位置 index，再用 `haystack.insert(index, needle)` 来插入新值。但你也可用 `insort` 来一步到位，并且后者的速度更快一些

- `bisect` 可以设置 `lo` 和 `hi` 缩小搜寻范围

- `bisect` 是 `bisect_right`的别名；有`bisect_left` 是插左边的

  
