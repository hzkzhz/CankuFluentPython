- 闭包指延伸了作用域的函数，其中包含函数定义体引用，但是不在定义体中定义的非全局变量，函数是不是匿名没有关系，关键是它能访问定义体之外定义的非全局变量

```python
def make_averager(): 
    series = []  # 
    def averager(new_value): 
        series.append(new_value) 
        total = sum(series) 
        return total/len(series) 
    return averager
```

> 在averager函数中，series是自由变量，未在本地作用域绑定的变量