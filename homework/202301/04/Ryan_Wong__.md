# p0283~0333 Functions as Objects III
 - 类型提示是python 3.6的新特性，用于描述函数因变量和返回值的类型建议，可通过Mypy这个静态类型检查工具来在编辑器中实现类型检查并补全类型提示。
 - 可用的类型提示
    - Any：任意类型变量可用，它不执行类型检查，可用作未知变量的紧急出口
    - 简单类型：如str、int、float等
    - Optional和Union：Union是联合类型，Union[X, Y]表示非X类型即Y类型，Optional[X]等价于Union[X, None]
 - 胜多负少的
