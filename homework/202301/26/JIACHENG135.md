- Array
    - 快
        <p>A quick experiment shows that it takes about 0.1 seconds for array.fromfile to load 10 million double-precision floats from a binary file created with array.tofile. That is nearly 60 times faster than reading the numbers from a text file, which also involves parsing each line with the float built-in. </p>

- 如何自定义 key 不在 dict里时的行为
    - `self.keys()` 返回一个`frozenset`

    ```python
    class StrKeyDict0(dict):
        def __missing__(self, key): 
            if isinstance(key, str):
                raise KeyError(key) 
            return self[str(key)]
        def get(self, key, default=None): 
            try:
                #这里call __getitem__ 触发 __missing__
                return self[key] 
            except KeyError:
                return default
        def __contains__(self, key):
            return key in self.keys() or str(key) in self.keys()
    ```