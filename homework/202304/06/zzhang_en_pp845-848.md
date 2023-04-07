# Fluent Python: pp 845-848

#### Computed Properties

Event这个class下有个speaker property，但我们还能从speaker取到speaker所在的所有Event class。

##### Step 1: Data-Driven Attribute Creation

实现了Record 类

- 直接从输入的kwargs dictionary来作为object的properties

    ```
    def __init__(self, **kwargs):
    	self.__dict__.update(kwargs)
    ```

实现了 load类

- 取到内容后，会存在一个字典里

    ```python
    # 取到 record_type, raw_records
    records = {}
    for raw_record in raw_records:
      key = f"{record_type}.{raw_record["serial"]}"
      records[key] = Record(**raw_record) # ~如何取这个内容构造一个Record
    ```

