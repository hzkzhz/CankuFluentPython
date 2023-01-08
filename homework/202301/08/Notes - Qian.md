### 使用Unicode排序算法排序 - pyuca.Collator.sort_key 方法,  只支持 Python 3.x
这样做更友好，而且恰好可用。
```
import pyuca
coll = pyuca.Collator()
fruits = ['caju', 'atemoia', 'cajá', 'açaí', 'acerola']
sorted_fruits = sorted(fruits, key=coll.sort_key)
sorted_fruits

Output: ['açaí', 'acerola', 'atemoia', 'cajá', 'caju']
```
