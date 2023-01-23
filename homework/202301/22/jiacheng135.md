- `namedtuple` 用法
    ```python
    collections.namedtuple('Card', ['rank', 'suit'])
    ```
    ```bash
    >>> beer_card = Card('7', 'diamonds')
    >>> beer_card
    Card(rank='7', suit='diamonds')
    ```

- `__getitem__` example


    ```python
    class FrenchDeck:
        def __getitem__(self, position): 
            return self._cards[position]
    >>> deck[0]
    Card(rank='2', suit='spades') 
    >>> deck[-1]
    Card(rank='A', suit='hearts')
    ```

    - 切片（slicing）也自动支持了
    - 基于iterator的reversed 也支持
