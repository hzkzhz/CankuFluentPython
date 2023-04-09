# Fluent Python pp 848-850

##### Step 2: Property to Retrieve a Linked Record

-  建一个static 的 fetch函数

    ```python
    @staticmethod
    def fetch(key):
      if Record.__index is None:
        Record.__index = load() # JSON => object values
      return Record.__index[key] # 取对应的record
    ```

- Event里的Venue property

    ```python
    class Event(Record):
      @property
      def venue(self):
        key = f"venue.{self.venue_serial}"
        return self.__class__.fetch(key) # 注意这里！
    ```

    - 避免了bug: 如果一个event record有一个key叫做fetch，直接用`self.fetch(key)`会调用event方法，而不是它父类Record的fetch方法，

    

