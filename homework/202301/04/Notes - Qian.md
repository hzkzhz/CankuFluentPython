## 处理UnicodeDecodeError
- 使用错误的编解码器可能出现鬼符或抛出 UnicodeDecodeError
- `octets.decode('utf_8', errors='replace')` 使用 'replace' 错误处理方式，\xe9 替换成了“�”(码位是 U+FFFD)，这是官方指定
的 REPLACEMENT CHARACTER(替换字符)，表示未知字符。

## BOM:有用的鬼符
UTF-8 的一大优势是，不管设备使用哪种字节序，生成的字节序列始终一致，因此不 需要 BOM。尽管如此，某些 Windows 应用(尤其是 Notepad)依然会在 UTF-8 编码的文 件中添加 BOM;而且，Excel 会根据有没有 BOM 确定文件是不是 UTF-8 编码，否则，它 假设内容使用 Windows 代码页(codepage)编码。

写入文件时指定了 UTF-8 编码，但是读取文件时没有这么做，因此 Python会出现decode失败的问题。
