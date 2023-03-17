### nolocal声明

> 用于说明变量是闭包里面声明的变量

```python
def make_averager(): 
    count = 0 
    total = 0 
    def averager(new_value): 
        nonlocal count, total #如果不用nonlocal下面会定义局部变量count
        count += 1 
        total += new_value 
        return total / count 
    return averager
```



