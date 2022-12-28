# Fluent Python: pp 70-80

集合的操作等略

### 3.9 dict 和 set 的背后

有 1000 万个双精度浮点数的数组，名叫 haystack。另外还有一个包含了 1000 个浮点数的 needles 数组，其中 500 个数字是从 haystack 里挑出来的，另外 500 个肯定不在 haystack 里。

- 如果用 `dict.fromkeys()` 建立haystack字典，用 `in` 搜：增长10000x数据量，时间只增长1.67x

- 如果把haystack换成set 和 list类型：set：(2.71x)，set交集: (3.61x)，list：(9279.9x)

#### 3.9.2 字典中的散列表

散列表是一个稀疏数组

- 散列表里的单元通常叫做 表元(bucket)
- 在dict的散列表中，每个key-value pair都占用一个bucket
- Python会设法保证大概还有1/3的表元是空的

Hash:

- 越是相似但不想等的对象，hash值的差别应该更大
- `str`, `bytes`, `datetime` 在计算hash的时候会随机加盐，防止DOS攻击
- 如果有一个整型对象，而且它能被存进一个机器 字中，那么它的散列值就是它本身的值。

- 在散列冲突的情况下，用 C 语言写的用来打乱散列值位的算法叫 perturb。
- 现实中，冲突的情况不多

#### 3.9.3 dict的实现及其导致的结果

1. key必须可hash（不变，支持`__eq__()`）
2. dict内存开销很大（散列表要求稀疏）：
   - 在用户自定义类型中可以用 `__slots__` 属性改变实例属性的存储方式，由dict变成tuple/
3. dict查询很快
4. key的次序取决于添加顺序（可能有冲突，会被换到别的位置）
   - 但是由`dict([key1, value1), (key2, value2)]`和`dict([key2, value2], [key1, value1])`得到的两个字典，在进行比较的时候，它们是相等的

5. 添加新key可能会改变已有key的顺序，取决于字典背后的实现
6. `.keys()`、`.items()` 和 `.values()` 方法返回的都是字典视图，更像集合，而不是列表。 视图还有动态的特性，它们可以实时反馈字典的变化。


