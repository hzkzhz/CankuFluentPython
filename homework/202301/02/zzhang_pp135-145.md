# Fluent Python: pp 135 - 145

#### 5.10.2 使用 `functools.partial` 冻结参数

例子1：normalize

```python
nfc = functools.partial(unicodedata.normalize, 'NFC')
```

例子2: 带定位参数的

```python
picture = partial(tag, 'img', cls='pic-frame')
```



## Ch 6: 使用一等函数实现设计模式

省略code，这几页主要介绍了一下要用的例子：

- Promotion 是 abstract基类，FidelityPromo, BulkItemPromo, LargeOrderPromo继承Promotion，实现 discount()方法；Order 类是 Promotion的上下文，包含total() 和 due() 两个方法

abstract类：

```python
from abc import ABC, abstractmethod
class Promotion(ABC):
    @abstractmethod
    def discount(self, order):
      	"""返回折扣金额（正值）"""
    
class Promotion(metaclass=ABCMeta):
  	...
```

