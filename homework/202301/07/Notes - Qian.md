# Extreme “Normalization”: Taking Out Diacritics - 就是那些在字母上方的声调
```
def shave_marks(txt):
"""去掉全部变音符号"""
norm_txt = unicodedata.normalize('NFD', txt) ➊ shaved = ''.join(c for c in norm_txt
if not unicodedata.combining(c)) ➋ 
  return unicodedata.normalize('NFC', shaved) ➌
➊ 把所有字符分解成基字符和组合记号。 
➋ 过滤掉所有组合记号。
➌ 重组所有字符。
```


`if unicodedata.combining(c) and latin_base:` - 基字符为拉丁字母时，跳过组合记号。

# Unicode文本排序
### Python比较非ASCII字符时，可能会出错，导致排序结果有误。所以，我们可以使用 locale.strxfrm 函数做排序键。
- 使用 locale.strxfrm 函数做排序键之前，要调用 setlocale(LC_COLLATE, «your_locale»)
```
fruits = ['caju', 'atemoia', 'cajá', 'açaí', 'acerola']
sorted_fruits = sorted(fruits, key=locale.strxfrm)
```
