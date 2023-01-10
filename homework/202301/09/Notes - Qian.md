# 支持字符串和字节序列的双模式API
标准库中的一些函数能接受字符串或字节序列为参数，然后根据类型展现不同的行为。re和os模块中就有这样的函数。
```
`re_numbers_str` = re.compile(r'\d+') ➊
re_words_str = re.compile(r'\w+') # 前两个正则表达式是字符串类型
`re_numbers_bytes` = re.compile(rb'\d+') ➋ 
re_words_bytes = re.compile(rb'\w+') # 后两个正则表达式是字节序列类型。

print(' str :', re_numbers_str.findall(text_str)) # 字符串模式 r'\d+' 能匹配泰米尔数字和 ASCII 数字。
```

## os函数中的字符串和字节序列
`GNU/Linux 内核不理解 Unicode!!!`
对任何合理的编码方案来说，在文 件名中使用字节序列都是无效的，无法解码成字符串。在不同操作系统中使用各种客户端 的文件服务器，在遇到这个问题时尤其容易出错。
