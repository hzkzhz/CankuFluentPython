# 909以后 python元编程-使用元类控制实例的创建

 - 通过重写type的方法实现禁止创建实例
 ```python3
 class NoInstances(type):
    def __call__(self, *args, **kwargs):
        raise TypeError("Can't instantiate directly")

# Example
class Spam(metaclass=NoInstances):
    @staticmethod
    def grok(x):
        print('Spam.grok')
        
  >>>Spam.func(42)
  Spam.func
  >>>s = Spam()
  TypeError: Can't instantiate directly
    raise TypeError("Can't instantiate directly")
Line 3 in __call__ (Solution.py)
    s = Spam()
Line 13 in <module> (Solution.py)
 ```
 
 - 通过重写type的方法实现单例
 ```python3
 class Singleton(type):
    def __init__(self, *args, **kwargs):
        self.__instance = None
        super().__init__(*args, **kwargs)

    def __call__(self, *args, **kwargs):
        if self.__instance is None:
            self.__instance = super().__call__(*args, **kwargs)
            return self.__instance
        else:
            return self.__instance

# Example
class Spam(metaclass=Singleton):
    def __init__(self):
        print('Creating Spam')
        
  if __name__=='__main__':
    a = Spam()
    b = Spam()
    if b is a:
        print("True")
    c = Spam()
    if c is a:
        print("True")
  '''
  Creating Spam
  True
  True
  '''
 ```
