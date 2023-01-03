# 文本和字节序列
`.encode()` - translate code to machine code/ utf8
`.decode()` - tranlaste machine code to code
`bytes()` and `bytearray` - 以从 string 对象使用给定的编码构建, 切片

## 几个处理 Unicode 数据的方法(包括 casefold、isdecimal、isidentifier、isnumeric、isprintable 和 encode


## one integer include two utf8
```
import array

numbers = array.array('h', [-2, -1, 0, 1, 2]) 
octets = bytes(numbers)
print(octets)

b'\xfe\xff\xff\xff\x00\x00\x01\x00\x02\x00' ➌
```
