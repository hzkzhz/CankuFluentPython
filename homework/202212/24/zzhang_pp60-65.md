# Fluent Python: pp 60-65

第三章

依旧是setdefault

`my_dict.setdefault(key, []).append(new_value)`

- 查找key对应的列表，如果没有的话返回一个空列表；append新value



### 3.4 映射的弹性键查询

`defaultdict` 是`dict` 的子类，自己实现了`__missing__`方法


#### 3.4.1 defaultdict: 处理找不到键的一个选择

建立defaultdict的时候可以设置一个`deafult_factory`:

```python
index = collections.defaultdict(list)
```

- 把 list 构造方法作为 default_factory 来创建一个 defaultdict。

- 如果在创建 defaultdict 的时候没有指定 default_factory，查询不存在的键会触发

  KeyError。

-  default_factory 只会在 `__getitem__` 里被调用. dd 是个 defaultdict，k 是个找不到的键， dd[k] 这个表达式会调用 default_factory 创造某个默认值，而 dd.get(k) 则 会返回 None。

#### 3.4.2 特殊方法 `__missing__`

- 也只会被`__getitem__` 调用，对`get`和`__contains__` **没有**影响。

如果Key是string，但是查的时候用了数字之类的，可以用`StrKeyDict0`处理，例子：

```python
class StrKeyDict0(dict):
  def __missing__(self, key):
      if isinstance(key, str): # 这个测试是必须的，否则会循环调用 __missing__
          raise KeyError(key) 
      return self[str(key)]
	def get(self, key, default=None):
      try:
          return self[key]
      except KeyError: 
          return default
  def __contains__(self, key):
			return key in self.keys() or str(key) in self.keys()
# -----------
d = StrKeyDict0([('2', 'two'), ('4', 'four')])
d[4]
# 'four'
```

