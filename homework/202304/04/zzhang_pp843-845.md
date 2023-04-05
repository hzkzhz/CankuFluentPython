# Fluent Python: pp 843 - 845

##### Flexible Object Creation with `__new__`

- 一些逻辑：`__init__` 的第一个参数是`self`，所以其实调用之前这个object已经在了，它是一个initializer

- 如果要construct，用`__new__`，有返回值（即新的object）

- 用途：根据参数构造不同的object

    ```python
    def __new__(cls, arg):
      if isinstance(arg, abc.Mapping):
        return super().__new__(cls)
      elif isinstance(arg, abc.MutableSequence):
        return [cls(item) for item in arg]
      else:
        return arg
    ```

    - 一般`__new__`的第一个参数是class自己
    - 默认的`__new__`行为就是把它delegate给`__new__`的superclass（比如object class），call的是`object.__new__(FrozenJSON)`=> 生成的object其实是FrozenJSON的实例

