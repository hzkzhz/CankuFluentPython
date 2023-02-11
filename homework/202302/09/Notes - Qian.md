# 接口:从协议到抽象基类

### 11.1 Python文化中的接口和协议
- Python 语言没有 interface 关键字，而且除了抽象基类，每个类都有接口
- 类实现或继承的公开属性，如 __getitem__ 或 __add__。


###
 __getitem__() is a magic method in Python, which when used in a class, allows its instances to use the [] (indexer) operators.
 ```
 class Test(object):
      
    # This function prints the type
    # of the object passed as well 
    # as the object item
    def __getitem__(self, items):
        print (type(items), items)
  
# Driver code
test = Test() 
test[5] # <class 'int'> 5
test[5:65:5] # <class 'slice'> slice(5, 65, 5)
test['GeeksforGeeks'] # <class 'str'> GeeksforGeeks
test[1, 'x', 10.0] # <class 'tuple'> (1, 'x', 10.0)
test['a':'z':2] # <class 'slice'> slice('a', 'z', 2)
test[object()] # <class 'object'> <object object at 0x7f75bcd6d0a0>
 ```
