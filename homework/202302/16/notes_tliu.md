# notes

看完了 design pattern 的剩下部分, 感觉没有太多的内容. 还是在强调很多 design pattern 对 python 都不是很适用. 要么已经有内嵌实现, 要么没有太大的意义.

唯一一个有趣的知识是: 一个函数显然是 callable 的, 那么它就可以调用 __call__ 方法. 然后这个方法也是 callable 的, 所以它也可以调用 __call__ 方法. 最后就可以:

```python
def chicken():
    return 'eggs'

chicken.__cal__.__call__.__call__()
>>> 'eggs'
```