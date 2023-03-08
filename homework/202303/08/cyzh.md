- 使用装饰器改进策略模式

```python
promos = [] # 起始列表为空
def promotion(promo_func): 
    promos.append(promo_func)  # 每次运行都会加入到promos中
    return promo_func 

# 三个策略
@promotion 
def fidelity(order): 
    return order.total() * .05 if order.customer.fidelity >= 1000 else 0 

@promotion 
def bulk_item(order): 
    discount = 0 
    for item in order.cart: 
        if item.quantity >= 20: 
            discount += item.total() * .1 
    return discount 

@promotion 
def large_order(order): 
    distinct_items = {item.product for item in order.cart} 
    if len(distinct_items) >= 10: 
        return order.total() * .07 
    return 0

# 选择最佳策略
def best_promo(order):
    return max(promo(order) for promo in promos)
```

