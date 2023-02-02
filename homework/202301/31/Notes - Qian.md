# A Default Parameter Value
- 'f'{parameter_name}''
```
def show_count(count, singular, plural):
    if count == 1:
        return f'1 {singular}'
    count_str = str(count) if count else 'no'
    if not plural:
        plural = singular + 's'
    return f'{count_str} {plural}'
```
