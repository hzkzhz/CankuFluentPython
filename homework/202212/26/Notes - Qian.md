# Queue in Python
同步的、线程安全的队列类，包括FIFO（先入先出)队列Queue，LIFO（后入先出）队列LifoQueue，和优先级队列PriorityQueue。这些队列都实现了锁原语，能够在多线程中直接使用。可以使用队列来实现线程间的同步。

##  queue.Queue(maxsize) initializes a variable to a maximum size of maxsize. 
- qsize() – Return the number of items in the queue.
- put_nowait(item) – Put an item into the queue without blocking. If no free slot is immediately available, raise QueueFull.
- get_nowait() – Return an item if one is immediately available, else raise QueueEmpty.

## 在Python中，队列是最常用的线程间的通信方法，因为它是线程安全的，自带锁。而Condition等需要额外加锁的代码操作，在编程对死锁现象要很小心，Queue就不用担心这个问题。
<img width="475" alt="Screen Shot 2022-12-27 at 12 04 59 AM" src="https://user-images.githubusercontent.com/73077953/209633436-2bb1cd32-1723-4453-b2db-c1885b8f0dc6.png">
