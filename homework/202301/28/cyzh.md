- `filter+map`与列表推导比较：
  
  ```python
>> symbols = '$¢£¥€¤' 
  >>> beyond_ascii = [ord(s) for s in symbols if ord(s) > 127] 
  >>> beyond_ascii 
  
  [162, 163, 165, 8364, 164] 
  
  >>> beyond_ascii = list(filter(lambda c: c > 127, map(ord, symbols))) 
  >>> beyond_ascii 
  
  [162, 163, 165, 8364, 164]
  ```
  
- 列表推导计笛卡尔积

  ```python
  >>> colors = ['black', 'white'] 
  >>> sizes = ['S', 'M', 'L'] 
  >>> tshirts = [(color, size) for color in colors for size in sizes] #先color 
  >>> tshirts 
  
  [('black', 'S'), ('black', 'M'), ('black', 'L'), ('white', 'S'),  
   ('white', 'M'), ('white', 'L')]
  ```

- % 格式运算符能匹配二元组

  ```python
  traveler_ids = [('USA', '31195855'), ('BRA', 'CE342567'), ('ESP', 'XDA205856')] 
  >>> for passport in sorted(traveler_ids): print('%s/%s' % passport)
  
  BRA/CE342567 
  ESP/XDA205856 
  USA/31195855
  ```

- *符号来获取不确定参数

  ```python
  >>> a, b, *rest = range(5) 
  >>> a, b, rest 
  (0, 1, [2, 3, 4]) 
  
  >>> a, b, *rest = range(3) 
  >>> a, b, rest 
  (0, 1, [2]) 
  
  >>> a, b, *rest = range(2) 
  >>> a, b, rest 
  (0, 1, [])
  ```

  

