# Fluent Python: pp 861-862

##### Properties Override Instance Attributes

一种情况：

```python
class Class:
	data = 'the class data attr'
```

- `vars(obj)` 返回这个实例的attribute（class里定义的attribute是另一回事）
- 但是如果直接 `obj.data` 可以输出class的attribute
- 如果直接更改`obj.data` 则只会更改obj的instance attributes，不会更改class的

另一种情况

```python
class Class:
	@property
	def prop(self):
		return 'the prop value'
```

- 不能直接更改instance的prop即`obj.prop='foo'` 会报错
- 需要通过`obj.__dict__['prop']='foo'` 来修改
- 但是`obj.prop` 还是显示的class的prop
- 但如果把class的prop值改了(`Class.prop='baz'`)，则`obj.prop` 得到值`'foo'`
    - 解释：重写`Class.prop` 摧毁了property object
    - 现在`obj.prop` 可以取回实例的属性。`Class.prop` 不再是一个property，所以不会overrides `obj.prop`.

