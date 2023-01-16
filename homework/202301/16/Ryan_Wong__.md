# p0393~0406 Class and Protocols I - 符合python风格的对象1

 - 这几节通过一个叫做Vector2d的class来讲述了定义一个功能完善的python风格类需要用到的python风格的方法，通过重写这些方法来实现自定义功能。包括：
    - 负责格式化打印类的__format__
    - 定义备选构造的装饰器@classmethod
    - 设置只读方法的装饰器@property
    - 把类对象hash化的手续（用到只读装饰器）
