# Notes

## slice
slice 更像是 cpp17 里面的 span view, 实现的是一个视图, 所以没有 copy 代价. 带来的问题就是需要比较注意深拷贝和浅拷贝的问题, 这在 cpp 中并不是问题. 甚至可以 del list[a:b] 把中间这部分删掉, 有点类似于 erase() 函数, 然后给定起始迭代器. 看起来 cpp 和 python 随着发展好的理念其实是大家都想要有的.

## using + and * in list
这个非常危险, 想起了经典的例子 [[0] * n] * n. python 经典 pitfall