# notes

namedtuple 和 data class 的主要区别在于是否有 mutable instances. 不过 data class 也可以通过
`@dataclass(frozen=True)` 来实现 immutable instances. 

asdict 是一个非常有用的函数. 在 cpp 中没办法做到这一点, 因为编译器根本不知道这些 fields 名字叫什么. 反射机制貌似还没有很好的解决方案.

在这里介绍了一种 injecting method 的方法. 假设现在有一个类 class Card, 我们可以自己写一个函数 foo

```
def foo(card):
    pass
```

然后我们可以 Card.some_function = foo. 然后 Card 的实例可以直接调用 foo() 函数, 不需要传参, 调用者就是参数.

这是因为 class 里面的函数本身第一个参数就是 self. 所以现在我们的 foo() 函数的参数 card 就会被当成是 self 来看待. 所以 a.some_function() 其实就是 some_function(a) 也就是 foo(card = a).

虽然作者并不推荐这种写法, 但是的确是一个有意思的知识点.
