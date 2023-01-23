# Fluent Python: pp 255-265

## Ch 11: 接口：从协议到抽象基类（ABC）

- 不建议编写抽象基类，容易过度设计

11.1

- 协议是非正式的接口，一个类可以只实现部分接口

11.2 以序列协议为例

- 只实现`__getitem__(self, pos)` 也可以支持 1）访问元素、2）迭代 和3）使用 in 运算符，而不用实现`__iter__` 或者 `__contains__`

11.3 使用猴子补丁在运行时实现协议（实现就地shuffle之前那个牌的class）

- 之前的代码如果直接调用`random.shuffle` 会出现 `FrenchDeck' object does not support item assignment` 的错误，因为`FrenchDeck` 只实现了*不可变的*序列协议 => 提供`__setitem__`方法

    ```python
    def set_card(deck, position, card):
      deck._cards[position] = card
    FrenchDeck.__setitem__ = set_card
    ```

    - 猴子补丁:在运行时修改类或模块，而不改动源码
        - 要处理隐藏和没有文档的部分（比如这里得知道 `FrenchDeck`有一个`_cards` 可变列表）

抽象基类的实用优势

- 可以使用 register 类方法 在终端用户的代码中把某个类“声明”为一个抽象基类的“虚拟”子类（只需满足底层语义契约，不用继承抽象基类）

通过一系列 if/elif isinstance 做检查通常不好，应该用多态，即采用一定的方式定 义类，让解释器把调用分派给正确的方法～

