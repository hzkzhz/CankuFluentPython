# Types Are Defined by Supported Operations

```
from collections import abc 
def double(x: abc.Sequence):
  returnx*2
```
This code causes an error because the Sequence ABC does not implement or inherit the __mul__ method. 

- Duck typing: is only enforced at runtime, when operations on objects are attempted. This is more flexible than nominal typing, at the cost of allowing more errors at run‐ time.
- Nominal typing: more rigid than duck typing, with the advan‐ tage of catching some bugs earlier in a build pipeline, or even as the code is typed in an IDE.

```
class Bird:
    pass
  
class Duck(Birdie):
    def quack(self):
        print('Quack!')
    
def bird_quack(birdie: Bird) -> None:
    birdie.quack()
   
def duck_quack(birdie: Duck) -> None:
    birdie.quack()
    
bird1 = Duck()
bird1.bird_quack()
bird1.duck_quack()
```
