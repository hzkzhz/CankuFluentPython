# Generic Mappings

<img width="588" alt="Screen Shot 2023-02-05 at 10 44 59 AM" src="https://user-images.githubusercontent.com/73077953/216838854-4263ce46-00f2-4973-a398-626ad84123d2.png">


# Abstract Base Classes
- Be conservative in what we send. The return value of a function is always a concrete object, so the return type hint should be a concrete type.
- typing.List: Useful for annotating return types. To annotate arguments it is preferred to use an abstract collection type such as Sequence or Iterable.
