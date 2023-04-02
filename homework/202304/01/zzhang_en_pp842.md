# Fluent Python: pp 842

The Invalid Attribute Name Problem:

- 不能见一个attribute跟Python保留keyword重复，比如`student.class` x
    - 但是可以`getattr(student, 'class')` 显式获取
