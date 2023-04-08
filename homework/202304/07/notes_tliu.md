# notes

lazy generate 很有意思，我们写这样一个代码：

```python
def gen_AB():
    print('start')
    yield 'a'
    print('continue')
    yield 'b'
    print('end')
```

如果我们用一个list来接它，那么就不会 lazy evaluate，而是直接把值一次性全都算出来了，所以输出语句是一次性全出来的。

但是如果我们用一个 tuple 来接，这个时候不会直接输出；而是在我们 for i in tuple 的时候才会输出出来。

所以这个时候的generate就是lazy的，等用到的时候才去真的计算。