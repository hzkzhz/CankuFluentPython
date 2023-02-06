- 学会用`bisect(haystack, needle)`在`hatstack`数组中查找第一个大于等于`needle`的位置
  
  - `bisect` 其实是`bisect_right`，反之还有`bitsect_left`
- `insort(seq,  item)` 把变量`item` 插入到序列`seq` 中，并能保持`seq` 的升序顺序
  - 它也有个变体叫`insort_left`
- 如果需要一个只包含数字的列表，`array.array` 比`list` 更高效，支持`pop`，`insert`，`extend`而且还支持从文件中读取和存入文件的方法：比如`frombytes` 和`tofile`。
