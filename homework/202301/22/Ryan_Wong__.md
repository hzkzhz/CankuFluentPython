# 0437~0460 Class and Protocols IV - 序列的特殊方法2
 书接上回继续讲实现一个完备的序列需要实现哪些属性和成员函数
 - 实现动态存取时，除了要实现__getattr__也要实现__setattr__，且两者行为需要一致。
 - 实现多个序列合并成tuple序列：zip(vector0, vector1, vector2, ...)。
 - 格式化：重新实现__format__方法，细则较多，建议本节作为字典查询。
