# Fluent Python: pp 850-860

Step 3: Property Overriding an Existing Attribute

Step 4: Bespoke Property Cache

Step 5: Caching Properties with functools

- `@cached_property`

忽略一大堆不想看的内容 -> p857

##### Using a Property for Attribute Validation 比较有用

- 还可以把public attribute转换成受getter和setter保护的attribute

- 比如防止一些attribute被设置为invalid的值

```python
@property
def weight(self):
  return self.__weight

@weight.setter
def weight(self, value):
  if value > 0:
    self.__weight = value
  else:
    raise ValueError('value must be > 0')
```

- 但造成了一部分repetition
- 用 property factory 或者 descriptor class 更好

##### A Proper Look at Properties

- `property` built-in是一个class

-  invoking a constructor 和  invoking a factory function没差别

- property 完整的signature：

    - ```python
        property(fget=None, fset=None, fdel=None, doc=None)
        ```

- 更改上面的两个函数模式

    ```python
    class xx:
    	def __init__(self, weight, ...):
        self.weight = weight
        ...
        
    	def get_weight(self):
        return self.__weight
      
      def set_weight(self, value):
        if value > 0:
          self.__weight = value
        else:
          raise ValueError('value must be > 0')
      weight = property(get_weight, set_weight)
    ```

    

    

