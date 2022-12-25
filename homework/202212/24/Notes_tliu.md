# Noets

## array ? list ?
list 可以包含多种数据类型, list 则类似于 c++ 里面的 std::vector<std::any>

array 可以比较好的利用数据特性对内存分布什么的进行优化
 
## NumPy 

Numpy 是用 c 和 少量 fortran 完成的一个庞大的库, 提供了非常多优秀的功能. 同时它在 C 语言层面也有比较多的接口, 所以如果要自己开发一个 python 库, 可以直接接入 numpy 提供的 C API, 这样不用再自己完全从最底层开始写起来