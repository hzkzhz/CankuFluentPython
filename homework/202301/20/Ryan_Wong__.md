# p0407~0422 Class and Protocols III - 序列的特殊方法1
 - 通过构造一个Vector类使其动作类似序列，来说明构造一个类所需的动作。
 - __init__() ： 使用别的list来初始化Vector
 - __len__：长度
 - __getitem__：随机读
 - 要用__getitem__来完美表示切片，就要使得sliced的返回值不是list而是Vector。
