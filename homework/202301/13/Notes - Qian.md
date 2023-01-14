# cls
使用名为 cls 的关键字参数传入“class”属性，这是一种变通方法，因为“class”是Python的关键字

```
def tag(cls=None, **attrs):
    if cls is not None:
        attrs['class'] = cls # the value of attrs is a class
```

# Some methods to generate HTML elements
```
tag('bar') # '<br />'

tag('p', 'hello') # <p>hello</p>

print(tag('p', 'hello', 'world')) 
# <p>hello</p>
# <p>world</p>

tag('p', 'hello', id=33)
# <p id="33">hello</p>

print(tag('p', 'hello', 'world', cls='sidebar'))
# <p class="sidebar">hello</p>
# <p class="sidebar">world</p>

tag(content='testing', name="img")
# '<img content="testing" />'

my_tag = {'name': 'img', 'title': 'Sunset Boulevard', 'src': 'sunset.jpg', 'cls': 'framed'}
tag(**my_tag)
# '<img class="framed" src="sunset.jpg" title="Sunset Boulevard" />'
```
