# Fluent Python: pp 868-877

##### Handling Attribute Deletion

如何删除property

```python
@property
def member(self):
  ...

@member.deleter
def member(self):
  ...
```

用call syntax则是

```python
member = property(member_getter, fdel=member_deleter)
```

如果不是property而是普通attribute，需要实现`__delattr__`

##### Essential Attributes and Functions for Attribute Handling

`__class__`: 找到实例的class，比如读`__getattr__`

`__dict__`: 存的writable attributes

`__slots__`: 写在class里的attribute，这样写能节省memory，不可新加attribute，slots和dict两者中只能有一个

##### Built-In Functions for Attribute Handling

- `dir([object])`
- `getattr(object, name[, default])`

- `hasattr(object, name)`
- `setattr(object, name, vlaue)`
- `vars([object])`

##### Special Methods for Attribute Handling

- both `obj.attr` and `getattr(obj, 'attr', 42)` trigger `Class.__getattribute__(obj, 'attr')`.
- 注意会从Class里拿

##### Soapbox

- replace constructors with factories
    - caching expensive object construction



