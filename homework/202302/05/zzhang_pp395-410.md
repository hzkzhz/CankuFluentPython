# Fluent Python: pp 395 - 410

16.7 yield from

- `main` 客户端
- `grouper` 委派生成器
- `averager` 子生成器

```python
from collections import namedtuple
Results = namedtuple('Result', 'count average')

# 子生成器
def averager():
  ...
  while True:
    term = yield # 读入新的value
    if term is None:
      break  # 返回average结果
    ...
  return Result(count, average) # 返回结果

# 委派生成器：相当于管道：把输入传给子生成器
def grouper(results, key):
  while True:
    results[key] = yield from averager() 
    # 每次创建一个averager实例
    # grouper发送的每个值都会经由yield from处理，通过管道传给averager实例
    # averager 运行结束后，返回的值绑定在key 上

# 客户端代码
def main(data): # data 包含 key:[values(floats)]
  results = {}
  for key, values in data.items():
    group = grouper(results, key)
    next(group)
    for value in values:
      group.send(value) # 传给grouper，最终到达averager 的 term=yield处，**grouper永远不知道传入的值是什么**
    group.send(None) # 结束当前的average实例，新建一个新的averager
```

委派生成器相关的异常处理：

- 传入委派生成器的异常，除了 `GeneratorExit` 之外都传给子生成器的 `throw()` 方法
- 传入 `GeneratorExit` ，则在子生成器调用`close()`

委派生成器详细伪代码（忽略其他异常处理）

```python
_i = iter(EXPR) # _i 是子生成器
try:
  _y = next(_i) # 预激
except StopIteration as _e:
  _r = _e.value # 如果直接就返回了，返回值就是result
else:
  while 1: 
    _s = yield _y # 子生成器生成元素_y，等待调用方发送 _s
    try:
      _y = _i.send(_s) # 转发给子生成器收到的_s
    except StopIteration as _e:
      _r = _e.value # 结束了，返回子生成器的返回值
      break
  RESULT = _r
```

- 更复杂的try-except 这里忽略，主要是处理子生成器没有throw方法，然后一些向上冒泡的东西

- 一般yield from示例几乎都使用asyncio模块做异步编程

16.9 使用案例：使用协程做离散事件仿真

- SimPy：实现离散事件仿真的包

出租车运营仿真（主要两个函数，`taxi_process` 协程，`Simulator.run`执行仿真）

```python
# taxi_sim.py
# Event = collections.namedtuple('Event', 'time proc action')

def taxi_process(ident, trips, start_time=0): 
  # ident: 编号，trips: 有多少段旅程
  time = yield Event(start_time, ident, 'leave garage')
  # 会接受仿真主循环送来的time
  for i in range(trips): 
    time = yield Event(time, ident, 'pick up passenger')
    time = yield Event(time, ident, 'drop off passenger')
  yield Event(time, ident, 'going home')
  # 结束
```

```python
# taxis = {i: taxi_process(i, (i+1) * 2, i * 5) for i in range(num_taxis)} # 新建协程相关的dict
# sim = Simulator(taxis)

class Simulator:
  def __init__(self, procs_map):
    self.events = queue.PriorityQueue() # 按时间保存Event
    self.procs = dict(procs_map) # 每一个identity对应一个协程
  
  def run(self, end_time):
    for _, proc in sorted(self.procs.items()):
      first_event = next(proc) # 预激活：离开车库
      self.events.put(first_event) # 保存到event pq里
    
    # 开始仿真
    while sim_time < end_time: # 如果因为时间到结束，会进入else block
      if self.events.empty():
        print("*** end of events ***")
        break # 因为没有时间而结束，不会进入else block
      
      current_event = self.events.get()
      sim_time, proc_id, previous_action = current_event
      print('taxi:', proc_id, proc_id * ' ', current_event)
      active_proc = self.procs[proc_id] # 找到这辆车队赢的协程
      next_time = sim_time + compute_duration(previous_action) # 计算这个action用的时间
      try:
        next_event = active_proc.send(next_time) # 让协程产生下一个事件
      except StopIteration:
        del self.procs[proc_id] # 如果已经结束了，就把这个协程删掉
      else:
        self.events.put(next_event) # 如果还有下面的event，就放入events里
      else:
        msg = '*** end of simulation time: {} events pending ***' # simulation时间到了
        print(msg.format(self.events.qsize()))
```

事件驱动型框架：

- 在单个线程中使用一个主循环驱动协程执行并发活动。使用协程做面向事件 编程时，协程会不断把控制权让步给主循环，激活并向前运行其他协程，从而执行各个并 发活动

- 协作式多任务:协程显式自主地把控制权让步给中央调度程序
- 而多线程实现的是抢占式多任务。调度程序可以在任何时刻暂停线程(即使在执行一个语句的过 程中)，把控制权让给其他线程。
