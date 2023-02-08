# Parameterized Generics and TypeVar
<img width="451" alt="Screen Shot 2023-02-07 at 11 53 57 PM" src="https://user-images.githubusercontent.com/73077953/217468154-6d18fc5c-7247-4102-97e5-780cbdee0713.png">

### Why Is TypeVar Needed?
It introduces type hints by adding the typing module and not changing anything else in the language.

With clever metaprogramming they could make the [] operator work on classes like Sequence[T]. But the name of the T variable inside the brackets must be defined somewhere

### Restricted TypeVar
TypeVar accepts extra positional arguments to restrict the type parameter.
