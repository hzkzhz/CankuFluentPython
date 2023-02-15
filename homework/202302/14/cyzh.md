- `defaultdict`：用于处理找不到键的方法，会创建一个新键，值为默认值
  - `defaultdict` 里的`default_factory` 只会在`__getitem__` 里被调用，在其他的
    方法里完全不会发挥作用。比如，`dd` 是个`defaultdict`，`k` 是个找不到的键，
    `dd[k]` 这个表达式会调用`default_factory` 创造某个默认值，而`dd.get(k)` 则
    会返回`None`。
