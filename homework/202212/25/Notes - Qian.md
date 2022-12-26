# 双向队列和其他形式的队列
所有的操作都是双向的。
![Screen Shot 2022-12-25 at 7 48 35 PM](https://user-images.githubusercontent.com/73077953/209497497-6fd5d4b4-cc6e-4753-a386-354f6e0d7263.png)

双向队列也付出了一些代价，从队列中间删除元素的操作会慢一些，因为它只对在头尾的操作进行了优化!!!


# multiprocessing.JoinableQueue类型是设计给进程间通信用的。
可以让任务管理变得更方便。它跟queue.Queue 类似。
