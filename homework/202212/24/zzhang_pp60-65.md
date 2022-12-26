# Fluent Python: pp 60-65

第三章

依旧是setdefault

`my_dict.setdefault(key, []).append(new_value)`

- 查找key对应的列表，如果没有的话返回一个空列表；append新value



### 3.4 映射的弹性键查询

`defaultdict` 是`dict` 的子类，自己实现了`__missing__`方法

