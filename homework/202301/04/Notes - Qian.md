## 处理UnicodeDecodeError
- 使用错误的编解码器可能出现鬼符或抛出 UnicodeDecodeError
- `octets.decode('utf_8', errors='replace')` 使用 'replace' 错误处理方式，\xe9 替换成了“�”(码位是 U+FFFD)，这是官方指定
的 REPLACEMENT CHARACTER(替换字符)，表示未知字符。
