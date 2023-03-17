

### 7.8标准库中的装饰器
> Python内置来三个用于装饰函数，property、classmethod、staticmethod。还有一个常见的装饰器是functools.wraps，它的作用是**协助构建**行为良好的装饰器。还有就是lru.cache和singledispatch

#### 7.8.1使用functools.lru_cache做备忘
> 实现备忘功能，一向优化技术

```python
import functools
from clockdeco import clock

@functools.lru_cache() 
@clock
def fibonacci(n):
	if n < 2:
		return n
	return fibonacci(n - 2) + fibonacci(n - 1)

if __name__=='__main__':
	print(fibonacci(6))
		
```
> 当我们引入functools.lru_cache() 后，fib函数不会重复计算参数同的值

**functools.lru_cache(maxsize=128, typed=False)**：maxsize是指定存储多少个调用结果，应该是2的幂。typed设置为True，会把不同参数类型的结果分开保存
