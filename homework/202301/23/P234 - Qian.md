# High-Order Functions
reduce(), filter(), map(), and apply() are best know high-order functions.

```
def reverse(word):
    return word[::-1]
    
fruits = ['strawberry', 'fig', 'apple', 'cherry', 'raspberry', 'banana']
sorted(fruits, key=reverse) # function work as an object.
```

## Modern replacements for map, filter, and reduce
```
example1 = list(map(factorial, range(6)) # build a list of factorials from 0! to 5!
print(example1) # [1,1,2,6,24,120]
example2 = map(factorial, range(6)) 
print(example2) # <map object at 0x7f7d8e96db70>
```
