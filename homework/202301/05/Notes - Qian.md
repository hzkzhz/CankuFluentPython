# 处理文本文件
处理文本的最佳实践是“Unicode 三明治”:
1. convert bytes to str; 
2. operations on str; 
3. convert str to bytes.
The principle here is to do the first step as early as possible and do the third step as late as possible. Most web frameworks uses UTF-8 for string manipulation.

#### You should read the file using the same encoding method as writing the file. Explicitly declare the encoding method when reading a file.





