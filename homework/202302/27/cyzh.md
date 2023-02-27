提取函数签名

```python
>>> from clip import clip 
>>> from inspect import signature 
>>> sig = signature(clip) #返回一个Signature 对象
>>> sig  # doctest: +ELLIPSIS 
<inspect.Signature object at 0x...> 

>>> str(sig) 
'(text, max_len=80)' 

>>> for name, param in sig.parameters.items(): 
...     print(param.kind, ':', name, '=', param.default) 
... 
POSITIONAL_OR_KEYWORD : text = <class 'inspect._empty'> 
POSITIONAL_OR_KEYWORD : max_len = 80
```

