# namedtuple

### It allow you to access their values using descriptive field names and the dot notation
```
from collections import namedtuple

Point = namedtuple("Point", "x y")
point = Point(x=2, y=4)
print(point.x, point.y) # 2, 4
```

<img width="1135" alt="Screen Shot 2023-01-28 at 10 24 19 PM" src="https://user-images.githubusercontent.com/73077953/215309097-be72b58e-004e-4447-8d2d-0a202fc09f80.png">
