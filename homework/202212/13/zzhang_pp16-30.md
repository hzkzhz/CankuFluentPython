## Ch 2: 序列构成的数组

Python 会忽略 代码里 [], {} 和 () 中的换行

#### Ch 2.2.2 列表推导同`filter`和`map`的对比

```python
symbols = ["$$#!#"]
# 列表推导
A = [ord(s) for s in symbols if ord(s) > 127]
# filter + map
A = list(filter(lambda c: c > 127, map(ord, symbols)))
```

- 其实两个的速度其实差不多

#### Ch 2.2.4 生成器表达式

- 生成器表达式的语法和列表推导差不多，只不过把方括号换成圆括号而已

- 内存里不会留下6个组合的列表，因为生成器表达式会在每次for 循环运行时才生成一个组合。

```python
colors = ['B', 'W']
sizes = ['S', 'M', 'L']
for tshirt in ('%s %s' % (c, s) for c in colots for s in sizes):
  print(tshirt)
```

#### 2.3.2 元组拆包

可以用 * 星号运算符把一个可迭代对象拆开作为函数的参数

``` python
>>> divmod(20, 8)
(2,4)
>>> t = (20, 8)
>>> divmod(*t)
(2,4)
>>> quotient, remain
```

可以用 *args 来获取不确定数量的参数

```python
>>> a, b, *rest = range(5)
>>> a, b, rest
(0, 1, [2, 3, 4])
```

#### 2.3.4 具名元组

`collections.namedtuple` 是一个工厂函数，它可以用来构建一个带字段名的元组和一个有名字的类 ——这个带名字的类对调试程序有很大帮助

```python
>>> from collections import namedtuple
>>> City = namedtuple("City", "name country population coordinations")
>>> # 两个参数：一个是类名，另一个可以是 由数个字符串组成的可迭代对象，或者是由空格分隔开的字段名组成的字符串
>>> tokyo = City('Tokyo', 'JP', 26.933, (35.689722, 139.691667))
>>> tokyo.population
36.933
>>> tokyo[1]
'JP'
```

继续上一个例子，注意 `_fields`, `_make(iterable)` 和 `_asdict()`

```python
>>> City._fields
('name', 'country', 'population', 'coordinates')
>>> LatLong = namedtuple('LatLong', 'lat long')
>>> delhi_data = ('Delhi NCR', 'IN', 21.935, LatLong(28.613889, 77.208889))
>>> delhi = City._make(delhi_data) # 相当于是 City(*delhi_data)
>>> delhi._asdict()
OrderedDict([('name', 'Delhi NCR'), ('country', 'IN'), ('population', 21.935), ('coordinates', LatLong(lat=28.613889, long=77.208889))])
>>> for key, value in delhi.as_dict().items():
...				print(key + ":", value)
name: Delhi NCR
country: IN
population: 21.935
coordinates: LatLong(lat=28.613889, long=77.208889)
```

#### 2.4.3 多维切片和省略

... 是Ellipsis对象的别名

`x[i,...]` 相当于 `x[i, :, :, :]`

