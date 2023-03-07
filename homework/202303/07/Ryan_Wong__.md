# 660~669 Generator - iterable reducing functions and yield from
 - all(it)当it中所有元素都不是假/0时返回True，否则（存在至少一个假/0）返回False。注意all([])是返回True的
 - any(it)当it中存在至少一个元素是真/非0时返回True，否则（全部元素是假/0）返回False。注意any([])是返回True的
 - reduce(func, it)需要一个2参数入口的函数func，对it的元素进行累计操作。
 - yield from 可以直接从嵌套的内层生成器中返回值。
