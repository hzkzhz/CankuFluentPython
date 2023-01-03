# Fluent Python: pp 145 - 155

#### 6.1.2 使用函数实现“策略”模式

- 策略实例没有状态，可以直接用 函数实现 代替
- 策略对象通 常是很好的享元(flyweight)
    - 享元是可共享的 对象，可以同时在多个上下文中使用
- 函数比用户 定义的类的实例轻量，而且无需使用“享元”模式



#### 6.1.3 选择最佳策略：简单的方式

用一个list 存 函数，然后iterate得到最优的结果。

这样实现的问题是，如果有新的策略，还得记得append到这个list里去



#### 6.1.4 找出模块中的全部策略

方法1:

- 用 内置函数 `globals()` （返回一个字典，表示当前的全局符号表；只针对定义函数/方法的模块）

```python
promos = [
  globals()[name] for name in globals()
  if name.endswith('_promo')
  and name != 'best_promo'
]
```



方法2:

- 在一个单独的模块中板寸所有策略函数，把 `best_promo` 排除在外

```python
# 导入 promotions 模块
# 导入 inspect模块
promos = [func for name, func in inspect.getmembers(promotions, inspect.isfunction)]
```

- `inspect.getmembers` 函数用于获取对象的属性

- 第二个参数 bool, optional. 这里只获取函数



### 6.2 “命令”模式

- 通常用来解藕 调用者和接受者
- 实现：在二者之间放一个 Command 对象，让它实现只有一个方法(execute) 的接口，调用接收者中的方法执行所需的操作。不同的接收者可以适应不同的 Command 子类。

简化：

- 不为调用者提供一个 Command 实例，而是函数
- 调用者不用调用 command.execute()，直接调用 command() 即可（实现`__call__`方法后）



杂谈

- 不是所有设计模式都能一成不变地在任何语言中运用



## Ch 7. 函数装饰器和闭包

- `nonlocal` 关键字



### 7.1 装饰器基础知识

装饰器替换函数：

```python
def deco(func):
		def inner():
      	print('runing inner()')
    return inner # 返回了新的函数
@deco
def target():
  	print("runing target()")

-------
>>> target()
# running inner()
```

target 是inner的引用 

- 元编程：在运行时改变程序的行为

装饰器特征

1. 能把被装饰得函数替换成其他函数
2. 装饰器在加载模块时立即执行
