# Positional-Only Parameters


# Packages for Functional Programming
### divmod(dividend, divisor) #  returns a tuple containing the quotient  and the remainder

### itemgetter # be used instead of the lambda function to achieve similar functionality.
- Performance: itemgetter performs better than lambda functions in the context of time.
- Concise: : itemgetter looks more concise when accessing multiple values than lambda functions.

```
from operator import itemgetter
for city in sorted(metro_data, key=itemgetter(1)): # sort by the attribute at index 1
  print(city) 
```
