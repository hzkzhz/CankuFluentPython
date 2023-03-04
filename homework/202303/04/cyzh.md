- 函数对象重构策略模式：先定义一个基类（策略类），然后定义多个子类（不同策略）。

```python
class Promotion(ABC):  # 策略：抽象基类 
    @abstractmethod 
    def discount(self, order): 
        
class FidelityPromo(Promotion):  # 第一个具体策略 
    """为积分为1000或以上的顾客提供5%折扣""" 
    def discount(self, order): 
        return order.total() * .05 if order.customer.fidelity >= 1000 else 0 

class BulkItemPromo(Promotion):  # 第二个具体策略 
    """单个商品为20个或以上时提供10%折扣""" 
    def discount(self, order):
        discount = 0
        for item in order.cart: 
            if item.quantity >= 20: 
                discount += item.total() * .1 
        return discount 

class LargeOrderPromo(Promotion):  # 第三个具体策略 
    """订单中的不同商品达到10个或以上时提供7%折扣""" 
    def discount(self, order): 
        distinct_items = {item.product for item in order.cart} 
        if len(distinct_items) >= 10: 
            return order.total() * .07 
        return 0
```

样例中定义Promotion为抽象类（Abstract Base Class），其他三个为子类