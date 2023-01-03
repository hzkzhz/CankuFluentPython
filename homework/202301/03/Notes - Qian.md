# 结构体和内存视图
- memoryview 类不是用于创建或存储字节序列的，而是共享内存，让你访 问其他二进制序列、打包的数组和缓冲中的数据切片，而无需复制字节序列。
```
with open('filter.gif', 'rb') as fp: # read binary
    img = memoryview(fp.read())
```
