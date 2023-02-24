# Fluent Python: pp 730-735

WSGI Application servers.

- client -> HTTP server ---(rout)--> applictaion server
    - WSGI: HTTP server + cache + task queue + periodic tasks

 Distributed message queue

- 没有新东西

Summary

- 有意思的点：threaded program涉及GIL的问题，但Python会定时interrupt threads

推荐的书：

- Advanced Python Development -- Matthew Wilkes: 看起来是有很多实际例子

- Parallel Programming with Python -- Jan Palach：standard lib + Celery

- The Little Book of Semaphores -- 一些有关thread和locks的难题（感兴趣🌟🌟🌟）
