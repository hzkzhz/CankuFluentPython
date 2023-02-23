# Fluent Python: pp 721 - 725

解析procs.py

- 用`0` 作为`poison pill` 让worker知道数据末尾
    - 在主loop里，每起一个进程都放入了0.
- worker也会push进 `PrimeResult(0, false, 0.0)` 让主loop知道这个worker完成工作了

常用的多进程实践：

- worker里loop indefinitely，遇到sentinel值退出循环
    - sentinel值怎么选？0，None，Ellipsis built-in object，但不能是object()因为需要serialize而且会有identity不一样的问题

选择process的个数

- 选跟CPU有多少核相同的数目，但实际实验做出来，超过CPU的核心数，median时间稍微高一点点或保持不变

