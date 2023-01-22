## 第一章：Python数据模型

**样例**：纸牌类

```python
import collections 
Card = collections.namedtuple('Card', ['rank', 'suit']) # 元组
class FrenchDeck:
    ranks = [str(n) for n in range(2, 11)] + list('JQKA') 	# 数字
    suits = 'spades diamonds clubs hearts'.split()	# 花色
    def __init__(self):
        self._cards = [Card(rank, suit) for suit in self.suits for rank in self.ranks]
 	def __len__(self):
 	    return len(self._cards)
 	def __getitem__(self, position):
 	    return self._cards[position]
    
# 可以用len来获取类的大小
deck = FrenchDeck()
len(deck)
>> 52

# deck[0],deck[-1]等可以直接获取第一张和最后一张，由 __getitem__ 方法提供的
deck[0]                                                                       
>> Card(rank='2', suit='spades')
deck[-1]
>> Card(rank='A', suit='hearts')

# 可以很容易获取一张随机张牌
In [5]: from random import choice          
In [6]: choice(deck)                                
Out[6]: Card(rank='K', suit='diamonds')
```

注：copy文档的python代码可能会出现缩进问题



