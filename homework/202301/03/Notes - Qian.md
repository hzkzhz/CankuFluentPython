# 结构体和内存视图
- memoryview 类不是用于创建或存储字节序列的，而是共享内存，让你访 问其他二进制序列、打包的数组和缓冲中的数据切片，而无需复制字节序列。
```
with open('filter.gif', 'rb') as fp: # read binary
    img = memoryview(fp.read())
```

# 基本的编解码器
 基本的编解: 'utf8'、'utf- 8' 和 'U8'
 ```
 for codec in ['latin_1', 'utf_8', 'utf_16']:
     print(codec, 'El Niño'.encode(codec), sep='\t')
 ```
 
 ## 处理UnicodeEncodeError
多数非 UTF 编解码器只能处理 Unicode 字符的一小部分子集。把文本转换成字节序列时， 如果目标编码中没有定义某个字符，那就会抛出 UnicodeEncodeError 异常，除非把 errors 参数传给编码方法或函数，对错误进行特殊处理。
There are several approaches to avoid error.
`city.encode('cp437', errors='ignore')`
`city.encode('cp437', errors='replace')`
`city.encode('cp437', errors='xmlcharrefreplace')`
