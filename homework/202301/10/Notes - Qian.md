# os函数中的字符串和字节序
`对任何合理的编码方案来说，在文 件名中使用字节序列都是无效的，无法解码成字符串。`
如果必须处理(也可能是修正)那些无法使用上述方式自动处理的文件名，可以把 字节序列参数传给 os 模块中的函数，得到字节序列返回值。
这一特性允许我们处理任何 文件名或路径名，不管里面有多少鬼符。
```
# 第二个文件名是“digits-of-π.txt”(有一个希腊字母 π)
os.listdir('.')
['abc.txt', 'digits-of-π.txt']
```

# Python 用作默认值的几个编码设置
locale. getpreferredencoding()、sys.getfilesystemencoding()、sys.getdefaultencoding()

