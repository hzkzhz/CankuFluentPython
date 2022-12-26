# p0125~0132 Dictionaries and Sets III

 - collections.OrderDict: key按照插入顺序排序的dict
 - collections.ChainMap: 若干个dict按照优先级排序链接起来的聚合dict，可以在外部dict直接用内部key读写对应value，如果多个内部dict拥有相同key，则外部dict的操作只影响优先级最高那个dict
 - collections.Counter: 对list或str使用的计数器，返回一个key为每个元素、value为每个元素计数的dict。支持most_common([n])操作，返回dict里面value最大的n个k-v组合。
 - collections.UserDict: 作为自定义dict的基类
 ```python3
 class CustomizedDict(collections.UserDict):
 ```
 - MappingProxyType: 创建dict的只读视图，可用于把内部映射暴露给只读的API。
 - .keys(), .values(), .items(): 创建dict的key、value、kv关系的只读视图。而且他们是iterable的，也就是可以直接从他们的实例中创建list
