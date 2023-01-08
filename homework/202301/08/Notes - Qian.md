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

# Unicode数据库
Unicode 标准提供了一个完整的数据库(许多格式化的文本文件)，不仅包括码位与字符 名称之间的映射，还有各个字符的元数据，以及字符之间的关系。例如，Unicode 数据库 记录了字符是否可以打印、是不是字母、是不是数字，或者是不是其他数值符号。`isidentifier、isprintable、isdecimal 和 isnumeric 等方法就是靠这些信息作判断的。`
