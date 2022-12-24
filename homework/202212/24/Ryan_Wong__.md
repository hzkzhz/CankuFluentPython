# p0111~0124 Dictionaries and Sets II

 - pattern matching with mappings：可以通过正则表达式的match来获得dict的指定键值对，应该是提供了粗略的语义分析功能？（不然想不出有什么用）
 - 字典推导：可用推导的形式互换kv、过滤k或v达不到标准的值（新建dict），假设已知dict名字为mp，新建mp1使得其kv倒转的写法如下：
 ```python3
 mp1 = {v: k for k, v in mp}
 ```
 - setdefault可用于设定查找不存在的key时返回的value，会让程序更高效。在dict里面没有默认值，但在defaultdict里面是预先设定好的
 - __missing__() 存在于dict的基类定义中，可通过重写的方式，使得查找不存在的key不会抛出错误（并自动填充自定义value）。
