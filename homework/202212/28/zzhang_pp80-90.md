# Fluent Python: pp 80-90

## Ch 4 文本和字节序列

### 4.1 字符问题

Unicode标准把字符的标识和具体的字节表述进行区分：

- 字符的**标识**：码位。Unicode标准中以4~6个十六进制数字表示，有前缀`U+`。比如A的码位是`U+0041`
- 字符的**具体表述**取决于编码。UTF-8编码中，A编码成单个字节 `\x41`，UTF-16LE中则为两个字节`\x41\x00`。欧元符号(`U+20AC`)在UTF-8中是三个字节，UTF-16LE中为两个字节。

### 4.2 字节

不可变`bytes`类型， 可变`bytearray`类型

- 除了`format`, `format_map` 和几个处理Unicode数据的方法之外，str类型的其他方法都支持`bytes`和`bytearray`类型
- 二进制序列有一个str没有的方法`fromhex`：`bytes.fromhex('31 4B CE 49')` 解析16进制数字对

构造方法：

- str + encoding
- 可迭代对象，提供0～255数值
- 实现了缓冲协议的对象（bytes, bytearray, memoryview, array.array）
- `memoryview` 对象允许在二进制数据结构之间*共享内存*

结构体 `struct` 和内存视图 `memoryview`

- `struct` 模块提供了一些函数，**把打包的字节序列转换成不同类型字段组成的元组**，还有 一些函数用于执行反向转换，把元组转换成打包的字节序列

- `memoryview` 类不是用于创建或存储字节序列的，而是共享内存，让你访 问其他二进制序列、打包的数组和缓冲中的数据切片，而无需复制字节序列

例子：

```python
import struct
fmt = "<3s3sHH" # 3s3s 两个3字节序列，HH两个16位二进制整数
with open('filter.gif', 'rb') as fp:
  	img = memoryview(fp.read()) # 用内存中的文件内容创建一个memoryview对象
header = img[:10] # 用切片创建一个memoryview对象，**不会**复制字节序列！
struct.unpack(fmt, header) # 拆包memoryview对象，得到一个元组，包含类型、版本、宽度、高度
# (b'GIF', b'89a', 555, 230)
del header # 删除引用，释放memoryview实例所占的内存
```



### 4.3 基本的编解码器

`latin1` 其他编码的基础

- 和`cp1252` 的字节值是一样的，码位都一样 



4.4 介绍了一些编码、解码时候遇到错误的解决方案。
