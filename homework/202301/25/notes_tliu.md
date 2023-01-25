# notes

我觉得这句话非常的有意思: duck typing 就是 objects 有类型, 但是 variable 没有类型. 非常的有哲理.

这一章剩下的部分感觉没有太多的意义.

下一章讲解 decorator, PEP318 中提到 decorator 这个名字非常有迷惑性, 这个我深有体会我一开始也不知道这是什么东西. 现在看到它其实是: use in compiler area—a syntax treeis walked and annotated. 

闭包: closures—which is what we get when functions capture variables defined outside of
their bodies.

```
@decorate
def target():
print('running target()')
```

等价于

```
def target():
print('running target()')
target = decorate(target)
```