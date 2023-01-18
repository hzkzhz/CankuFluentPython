# Choosing Between == and is
- While programming, we often care more about values than object identities, so == appears more frequently than is in Python code.
- if you are comparing a variable to a singleton, then it makes sense to use is. 
`x is None` or `x is not None`
- a == b is syntactic sugar for a.__eq__(b). But most built-in types override __eq__ with more meaningful implementations. Equality may involve a lot of processing when comparing large collections or deeply nested structures.

# The Relative Immutability of Tuples
- The immutability of tuples really refers to the physical contents of the tuple data structure and does not extend to the referenced objects. 简单地说就是，tuple整体不能变，但是它里面的元素如果是可以被修改的，那还是可以修改。
- Copies Are Shallow by Default
```
l1 = [3, [55, 44], (7, 8, 9)]
l2 = list(l1)
print(l1 == l2) # True
print(l1 is l2) # False
```
