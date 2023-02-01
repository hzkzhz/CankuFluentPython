# Fluent Python: pp 365 - 380

Ch 15: 上下文管理器和else块

15.1 `with`

- for后面跟 else：for 循环运行完了（没break），运行else里的
- while后面跟else：while因条件为假退出（没break），运行else里的
- try后面跟else：try里没有抛出异常，运行else里的 => after call相关的语句应该放在else里，try块里应该只抛预期异常的语句

15.2 上下文管理器和`with`

- with开始前会调用`__enter__`，结束后会在上下文管理器对象上调用`__exit__`

    - 例子：

        ```python
        with LookingGlass() as what: # __enter__ 返回的值绑定在what上
          print('Alice')
          print(what)
        # ceilA
        # YKCOWREBBAJ
        # >> what
        # JABBERWOCKY # what的值是JABBERWOCKY
        
        # LookingGlass的实现
        class LookingGlass:
          def __enter__(self):
            import sys
            self.original_write = sys.stdout.write
            sys.stdout.write = self.reverse_write # 替换原有的sys.stdout.write
            return 'JABBERWOCKY'
         	
         	def reverse_write(self, text):
            self.original_write(text[::-1])
          
          def __exit__(self, exc_type, exc_value, traceback):
            import sys
            sys.stdout.write = self.original_write # 恢复
            if exc_type is ZeroDivisionError:
              print('please do not divide by zero')
              return True
            # 如果 __exit__ 方法返回 None，或者 True 之外的值，with 块中的任何异常都会向上冒泡
        ```

        

15.3 `contextlib`模块中的实用工具

- `closing` 如果对象提供了 close() 方法，没有实现enter/exit，可以用它构建上下文管理器
- `suppress` 构建临时忽略指定异常的上下文管理器
- `@contextmanager` 把简单的生成器函数变成上下文管理器
- `ContextDecorator`: 基类，用于定义基于类的上下文管理器
- `ExitStack` 如果事先不知道 with 块要进入多少个 上下文管理器，可以使用这个类，例如，同时打开任意一个文件列表中的所有文件

15.4 `@contextmanager`

- 关键在yield语句

    - yield 语句前面的所有代码在 with 块开始时(`__enter__`) 执行

    - yield 的值绑定到with 语句中 as 子句的目标变量上

    - yield 语句后面的代码在 with 块结束时(`__exit__`)执行

- 注意yield 要用 try 来处理exception！如果不想让 `@contextmanager` 压制异常，必须在被装饰的函数中显式重新抛出异常

    - 使用 `@contextmanager `装饰器时，要把 yield 语句放在 try/finally 语句中 (或者放在 with 语句中)，这是无法避免的，因为我们永远不知道上下文管理器

        的用户会在 with 块中做什么
