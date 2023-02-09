# 633~636 Iterators II - Sentence类2
 - 可迭代对象（iterable）和迭代器（iterator）不同，前者包含后者。前者是一个含义很广的概念，所有可以循环遍历的结构，比如list、dict都是iterable。但iterator只是一个单向往前（往前过程中记录每一步位置）不能回头的游标。
 - 实现\_\_iter\_\_ 方法（该方法返回自身）就是iterable，在此基础上实现了 \_\_next\_\_ 方法的是iterator。
