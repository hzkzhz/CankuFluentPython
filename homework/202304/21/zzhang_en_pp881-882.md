# Fluent Python: pp 881-882

回顾property

````python
weight = quantity('weight')
def quantity(storage_name):
  def qty_getter(instance):
    return instance.__dict__[storage_name]
  
  def qty_setter(instance, value):
    ...
  
  retrun property(qty_getter, aty_setter)
````

<<descriptor>> Quantity:

- storage_name
- `__init__`
- `__set__`

LineItem class:

- descriotion
- weight {storage}
- price {storage}
- `__init__`
- Subtotal

descritptor class == manage ==> LineItem class

- Each instance of a descriptor class, declared as a class attribute of the managed class
- LineItem instances are the managed instances 
- **Storage attribute**: managed instance的性质，保存managed attribute，比如weight和price；他们两和descriptor instances不同
- **Managed attribute**: 在managed class中的public性质存storage attribute中的值，由descriptor instance负责，

