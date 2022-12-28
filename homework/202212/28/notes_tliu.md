# Human use test. Computers speak bytes.

虽然编码很烦, 但是用 numpy 的时候经常会用到编码之类的东西还是需要看一下.

尤其是当数据需要和 cpp 去交互的时候编码方式统一就非常重要了.

学到一个英文单词 G clef 高音谱号.

>>> s = 'café'
>>> len(s)
4
>>> b = s.encode('utf8')
>>> b
b'caf\xc3\xa9'
>>> len(b)
5
>>> b.decode('utf8')
'café'

这个例子很好的说明了 encode 和 decode 的作用.

只有 str 类型 slice of lenght == a single element