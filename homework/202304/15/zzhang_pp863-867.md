# Fluent Python: pp 863-867

改写class.data with new property

- `Class.data = property(lambda self: 'the "data" prop value.')`

`obj.data` 并不从自己的data开始找，而是从`obj.__class__`开始找，所以如果Class里面有property，实例`obj.data`会被shadow掉

##### Property Documentation

- `help()`输出的其实是`__doc__`属性

##### Coding a Property factory

- 用factory 去构造quantity properties: `weight=quantity('weight')`

- ```python
    def quantity(storage_name):
      
      def qty_getter(instance):
        return instance.__dict__[storage_name]
      
      def qty_setter(instance, value):
        if value > 0:
          instance.__dict__[storage_name] = value
        else:
          raise ValueError('value must be > 0')
      return property(qty_getter, qty_setter)
    ```

    
