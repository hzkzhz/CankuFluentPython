# How to use Unicode correctly and smartly?

- U+0301是COMBINING ACUTE ACCENT，加在“e”后面得到“é”。在Unicode标准中，'é'和 'e\u0301' 这样的序列叫“标准等价物”(canonical equivalent)，应用程序应该把它们视作相同的字符。
We can make use of this character.
- Try to avoid the confusion as 'é'和 'e` are absolutely different.
- Use unicodedata.normalize 函数提供的 Unicode 规范化
```
s1 = 'café'
s2 = 'cafe\u0301'
len(normalize('NFC', s1)), len(normalize('NFC', s2))
Output: (4, 4)

len(normalize('NFD', s1)), len(normalize('NFD', s2))
Output: (5, 5)
```

- 使用 NFC 时，有些单字符会被规范成另一个单字符。例如，电阻的单位欧姆(Ω)会被 规范成希腊字母大写的欧米加. 

# 大小写折叠: 把所有文本变成小写，再做些其他转换。
只包含 latin1 字符的字符串 s，s.casefold() 得到的结果与 s.lower() 一样，唯有两 个例外:微符号 'μ' 会变成小写的希腊字母“μ”(在多数字体中二者看起来一样);德语 Eszett(“sharp s”，ß)会变成“ss”。


# 规范化文本匹配实用函数
对大多数应用来说，NFC 是最好的规范化形式。不区分大小写的比较应该使用 str.casefold()。
```
s1 = 'café'
s2 = 'cafe\u0301'
s1 == s2 => Flase
nfc_equal(s1, s2) => True
nfc_equal('A', 'a') => False
```
