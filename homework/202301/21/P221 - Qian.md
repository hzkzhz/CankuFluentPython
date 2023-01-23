# collections.deque

collections.deque is a `thread-safe` double-ended queue. It provides the synchronized classes such as SimpleQueue, Queue, LifoQueeu, and PriorityQueue.
```
deque([1, 2, 3, 4, 5, 6, 7, 8, 9, 0], maxlen=10) # max length is 10
dq.appendleft(-1)
print(dq) # [-1, 1, 2, 3, 4, 5, 6, 7, 8, 9], add -1 and remove 0

dq.extend([11,22,33]) # append to the right and remove the first three elements.
print(dq) # [3, 4, 5, 6, 7, 8, 9, 11, 22, 33]

dq.extendleft([10,20,30,40]) # append to the left and remove the last four elements.
print(dq) # [40, 30, 20, 10, 3, 4, 5, 6, 7, 8]
```


