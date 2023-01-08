# Extreme “Normalization”: Taking Out Diacritics - 就是那些在字母上方的声调
```
def shave_marks(txt):
"""去掉全部变音符号"""
norm_txt = unicodedata.normalize('NFD', txt) ➊ shaved = ''.join(c for c in norm_txt
if not unicodedata.combining(c)) ➋ return unicodedata.normalize('NFC', shaved) ➌
➊ 把所有字符分解成基字符和组合记号。 
➋ 过滤掉所有组合记号。
➌ 重组所有字符。
```
