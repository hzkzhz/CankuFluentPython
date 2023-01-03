# Fluent Python: pp 125-135

### 5.7 从定位参数到仅限关键字参数

- 仅限关键字参数 (keyword-only argument) 
- 调用函数时使用 `*` 和 `**` 展开可迭代对象。
- 例子

```python
def tag(name, *content, cls=None, **attrs):
  	if cls is not None:
      	attrs['class'] = cls
    if attrs:
      	attr_str = ''.join(' %s="%s"' % (attr, value) 
                           for attr, value in sorted(attrs.items()))
    else:
        attr_str = ''
    if content:
      	return '\n'.join("<%s%s>%s</%s>" % (name, attr_str, c, name) 
                         for c in content)
    else:
        return '<%s%s />' % (name, attr_str)
# tag('br') => '<br \>'
# tag('p', 'hello') => '<p>hello</p>'
# tag('p', 'hello', id=33) => '<p id="33">hello</p>'
# tag('p', 'hello', 'world', cls='sidebar') => 
#           <p class="sidebar">hello</p>
#           <p class="sidebar">world</p>
# cls 一定要关键词参数指定
```

- 定义函数时若想指定仅限关键字参数（比如例子中的 `cls`），要把它们 放到前面有 * 的参数后面
- 如果不想支持数量不定的定位参数，但是想支持仅限关键字参 数，在签名中放一个 *
- 例子：`def f(a, *, b)`



### 5.8 获取参数的信息

Bobo example

```python
import bobo

@bobo.query('/')
def hello(person):
  	return 'Hello %s!' % person
```

Bobo 会内省 hello 函数， 发现它需要一个名为 person 的参数，然后从请求中获取那个名称对应的参数，将其传给 hello 函数

```
http://localhost:8080/?person=Jim
"Hello Jim!"
```

- 函数对象有`__defaults__`属性，值是元组，保存着定位参数和关键字参 数的默认值
- 仅限关键字参数的默认值在` __kwdefaults__ `属性中

- 参数的名称在` __code__ `属性中，它的值是一个 code 对象引用，自身也有很多属性

```python
# Example: def clip(text, max_len=80)
clip.__defaults__ # (80,)
clip.__code__ # <code object clip at 0x...>
clip.__code__.co_varnames # ('text', 'max_len', 'end', 'space_before', 'space_after')
clip.__code__.co_argcount # 2

```

- 参数名称在 `__code__.co_varnames `中， 不过里面还有函数定义体中创建的局部变量，参数名称由 `__code__.co_argcount ` 确定。default值从后往前匹配。

- 可以用`inspect.signature` 去看 参数及其默认值

```python
from inspect import signature
sig = signature(clip)
str(sig) # '(text, max_len=80)'
for name, param in sig.parameters.items():
		print(param.kind, ':', name, '=', param.default)
# POSITIONAL_OR_KEYWORD : text = <class 'inspect._empty'>
# POSITIONAL_OR_KEYWORD : max_len = 80
```

param.kind 五种类型：

1. `POSITIONAL_OR_KEYWORD`: 可以通过定位参数和关键字参数传入的形参
2. `VAR_POSITIONAL`: 定位参数元组
3. `VAR_KEYWORD`: 关键字参数字典
4. `KEYWORD_ONLY`: 仅限关键字参数
5. `POSITIONAL_ONLY` 仅限定位参数，Python声明函数的句法不支持，但有些使用C语言实现且不接受关键字参数的函数支持（如`divmod`)

`inspect.Signature` **bind**

- 把任意个参数绑定到签名中的形参上
- `sig.bind(**my_tag)` 其中 `my_tag` 是个自己定义的字典



### 5.9 函数注解

```python
def clip(text:str, max_len:'int > 0'=80) -> str:
	 pass
```

看 `'int > 0'` 的位置 和 `-> str` 的位置。

- Python 对注解所做的唯一的事情是，把它们存储在函数的 ` __annotations__ `属性里

- 一般适合IDE和lint程序等工具进行静态类型检查



### 5.10 支持函数式编程的包

#### 5.10.1 operator 模块

- 求和有 sum，求积没有 => 使用 reduce + lambda

  - `reduce(lambda a, b: a * b, range(1, n+1))`

  - operator 有各种算数符号比如 `mul` 就可以省去 lambda

- `itemgetter` 和 `attrgetter`  自行构建函数

  - `itemgetter(1)` 等于 `lambda fields: fields[1]`
  - `attrgetter('name', 'coord.lat')` 按照名称提取，如果有`.` 还会深入浅套对象

- `methodcaller` 会自动创建函数，创建的函数会在对象上调用参数指定的方法

  - ```python
    from operator import methodcaller
    s = 'The time has come'
    hiphenate = methodcaller('replace', ' ', '-')
    hiphenate(s) # 'The-time-has-come'
    ```

  - 上面例子表明 methodcaller 还可以冻结某些参数，和 `functools.partial`类似。
