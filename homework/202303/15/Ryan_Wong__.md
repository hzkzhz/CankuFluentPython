# 731~742 多线程使用方法

```python3
import itertools
import time
from threading import Thread, Event
def spin(msg: str, done: Event) -> None: #  done可控制该线程马上退出
    ... # 含有计时功能显示在spin内经过的秒数
def slow() -> int:
    seconds = 2
    time.sleep(seconds)
    return seconds
def main() -> None:
    done = Event()
    thread = Thread(target=spin, args=('thinking!', done))
    print(f'thread object: {thread}')
    thread.start()
    result = slow() # 主线程睡眠，GIL被副线程spin获取，result反映停止的时长
    done.set() # 发去信号量，终止spin线程，GIL被主线程重新获取
    thread.join()
    print(f'Answer: {result}') # spin打印的结果和result匹配，表示主线程睡眠的时间里副线程才能执行
if __name__=='__main__':
    main()
```
