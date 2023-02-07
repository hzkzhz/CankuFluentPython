# 623~633 Iterators I - Sentence类1
 - 要对凭空构造的Sentence类实现可迭代功能，要实现__iter__和__next__方法，如果对实例x能调用iter(x)不抛出异常，该类型即为可迭代。
 - 在py 3.6以前的版本还可通过实现__getitem__方法来实现可迭代功能，但是在之后的py版本可能取消。
