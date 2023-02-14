### The architecture of Exception in Python
<img width="411" alt="Screen Shot 2023-02-14 at 12 14 49 PM" src="https://user-images.githubusercontent.com/73077953/218851980-86df78bc-56a0-47e7-b7a8-e00574131b11.png">

# Abstract Base Class (abc) in Python
The main goal of the abstract base class is to provide a standardized way to test whether an object adheres to a given specification. It can also prevent any attempt to instantiate a subclass that doesn't override a particular method in the superclass. And finally, using an abstract class, a class can derive identity from another class without any object inheritance.

```
class AbstractClass(metaclass=abc.ABCMeta):
    def abstractfunc(self):
        return None

AbstractClass.register(dict)
print(issubclass(dict, AbstractClass))
```
```
import abc
  
class AbstractClass(metaclass=abc.ABCMeta):
    @abc.abstractmethod
    def abstractName(self):
        pass
  
class ValidSubClass(AbstractClass):
    def abstractName(self):
        return 'Abstract 1'
  
vc = ValidSubClass()
print(vc.abstractName())
```
