# 725~731 Concurency GIL基本概念
 - GIL（Global Interpreter Lock）是一个进程内的全局概念，同一进程任何时刻只有一个GIL，任何线程只有获得了GIL才能执行。每个线程都会经历“获得GIL-->执行代码直到挂起-->释放GIL”的过程。
 - 为防止GIL被某线程永久持有，每隔一段时间（缺省5min）python会产生一个中断来释放GIL，此时同进程内所有线程竞争这一个GIL。
 - CPU敏感的python代码推荐使用多进程而不是多线程，因为一个进程永远只能同时执行一个线程，且涉及到GIL的切换上下文开销很大。