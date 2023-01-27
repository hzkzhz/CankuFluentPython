- 使用namedtuple来build class
    ```python
    >>> from collections import namedtuple
    >>> Coordinate = namedtuple('Coordinate', 'lat lon') 
    >>> issubclass(Coordinate, tuple)
    True
    >>> moscow = Coordinate(55.756, 37.617)
    >>> moscow
    Coordinate(lat=55.756, lon=37.617)
    >>> moscow == Coordinate(lat=55.756, lon=37.617) 
    True

    ```

- `_make` build class from an iterable
    ```python
    >>> City._fields
    ('name', 'country', 'population', 'location')
    >>> Coordinate = namedtuple('Coordinate', 'lat lon')
    >>> delhi_data = ('Delhi NCR', 'IN', 21.935, Coordinate(28.613889, 77.208889)) 
    >>> delhi = City._make(delhi_data)
    >>> delhi._asdict()
    {'name': 'Delhi NCR', 'country': 'IN', 'population': 21.935,
    'location': Coordinate(lat=28.613889, lon=77.208889)}
    >>> import json
    >>> json.dumps(delhi._asdict())
    '{"name": "Delhi NCR", "country": "IN", "population": 21.935,
    "location": [28.613889, 77.208889]}'
    ```
