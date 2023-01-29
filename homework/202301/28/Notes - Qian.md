# methodcaller
### The operator module is a built-in module in Python. The module provides functions equivalent to the intrinsic operators of Python.

```
from operator import methodcaller

lst_pop = methodcaller('pop')
lst = [1,2,3,4]
popped_element = lst_pop(lst)
print("%s.pop() = %s" % (lst, popped_element))

element = 3
lst_count = methodcaller('count', element)
lst = [1, 2, 2, 3, 3, 3]
count_of_element = lst_count(lst)
print("%s.count(%s) = %s" % (lst, element, count_of_element))
```
