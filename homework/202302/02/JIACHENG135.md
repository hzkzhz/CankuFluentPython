- Using None as default
    ```python
    from typing import Optional
    def show_count(count: int, singular: str, plural: Optional[str] = None) -> str:
        return "
    ```
- python的类型检查可能会报一些在runtime没有问题的error，这看似很愚蠢，但是当callstack比较深的时候，靠runtime error long debug可能会比较痛苦，可以先用类型检查的output来debug，更舒适一些。 

- `Any` type支持所有operation，可以用Any来定向忽略那些不重要的部分，使得Type check更精准