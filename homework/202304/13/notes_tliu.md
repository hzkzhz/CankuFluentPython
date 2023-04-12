# notes

感觉 generator 充满了奇技淫巧，如果你想让他停下来并且给你一个返回值，你需要 gen.send(STOP)。然后这个东西会给你一个 StopIteration 异常，你想要这个值必须接这个异常。然后读取这个异常的 .value 字段才能获得返回值。

或者是你用一个 delegating generator ，用 yield from 也可以。

虽然看起来是一个奇技淫巧，是一个 hack，但是这是在官方文档里面的，写在 PEP 里的。

来到下一章。context manager。
开头的格言里大佬说 with 是一个非常重要的东西在python里，但是我完全没有感觉到。