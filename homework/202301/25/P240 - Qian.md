# From Positional to Keyword-Only Parameters
This is a magic for Python as it is often used for generating html elements. Using `*` and `**` parameters can unpack iterables.

`content can be used for one parameter, but attrs can be a list of parameters.`
```
def tag(name, *content, class_=None, **attrs): 
    if class_ is not None:
        attrs['class'] = class_
    attr_paris = (f' {attr}="{value}"' for attr, value in sorted(attrs.items()))
    attr_str = ''.join(attr_pairs)
    if content:
        elements = (f'<{name}{attr_str}>{c}</{name}>'
                    for c in content)
        return '\n'.join(elements)
    else:
        return f'<{name}{attr_str} />'
    
```
