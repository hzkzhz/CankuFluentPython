# A Default Parameter Value
- 'f'{parameter_name}{another_parameter_name}'', use this can return some default parameter value.
```
def show_count(count, singular, plural):
    if count == 1:
        return f'1 {singular}'
    count_str = str(count) if count else 'no'
    if not plural:
        plural = singular + 's'
    return f'{count_str} {plural}'
```

- def hex2rgb(color=str) -> tuple[int, int, int]
This is a good way to return some fixed values.

# Using None as a Default
def show_count(count: int, singular: str, plural: Optional[str] = `None`) #  Optional[str] means plural may be a str or None.


