# Defensive Programming with Mutable Parameters

# del and Garbage Collection
```
a = [1, 2] 
b = a # b is a pointer, a is a pointer, and they are binded to the same object.
del a # delete the pointer a, but the pointer b is still there.
print(b) # the object that b is pointing to is still there.
# [1, ]
```
