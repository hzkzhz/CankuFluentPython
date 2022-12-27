# NumPy
NumPy provides an array object that is up to 50 times faster than traditional Python lists. This is due to the locality of reference of NumPy array. It is stored in continuous place in memory.
```
import numpy
a = numpy.arrange(12)
```


# SciPy
SciPy is a scientific computation library that uses NumPy underneath. SciPy has optimized and added functions that are frequently used in NumPy and Data Science.

# Timsort
sorted 和 list.sort 背后的排序算法是 Timsort，它是一种自适应算法，会根据原始数 据的顺序特点交替使用插入排序和归并排序，以达到最佳效率。这样的算法被证明是 很有效的，因为来自真实世界的数据通常是有一定的顺序特点的。
