# Partial
Partial functions allow us to fix a certain number of arguments of a function and generate a new function.

```
from functools import partial

# A normal function
def f(a, b, c, x):
	return 1000*a + 100*b + 10*c + x

# A partial function that calls f with
# a as 3, b as 1 and c as 4.
g = partial(f, 3, 1, 4)

# Calling g()
print(g(5))
```

<img width="603" alt="Screen Shot 2023-01-30 at 12 50 45 PM" src="https://user-images.githubusercontent.com/73077953/215592579-ae48ee0d-5653-4f2b-a0be-cfa9bc099cdb.png">
