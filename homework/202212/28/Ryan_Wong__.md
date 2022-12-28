# p0133~0147 Dictionaries and Sets IV

 - python是有set类型的，将list类型的lst转为set的写法是 set(lst)
 - 可以通过&、&=、|、|=、-、-=等操作符实现两个set之间的交、并、差等操作。
 - 可以通过add()、discard()等方法实现添加、移除元素
 - 可以通过<、<=、>、>=等操作符判断set从属关系
 - 可以通过 in 来判断元素是否属于某set
 - 不同于cpp里set的红黑树，python3的set使用散列表，更类似于unordered_set，查询很快但内存开销十分巨大，而且新插入的元素有可能导致原有的元素被打乱顺序。
