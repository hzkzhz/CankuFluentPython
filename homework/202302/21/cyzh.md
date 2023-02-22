## 第四章：文本和字节序列

- 解码与编码

  ```python
  In [1]: s = 'cafe'                                                                                                   
  
  In [2]: len(s)                     
  Out[2]: 4
  
  In [3]: b = s.encode('utf8')
  In [4]: b                                    
  Out[4]: b'cafe'
  
  In [5]: b.decode('utf8')                       
  Out[5]: 'cafe'
  ```

- `bytes`和`bytearray`对象

  ```python
  In [6]: cafe = bytes('café', encoding='utf_8')                                     
  In [7]: cafe
  Out[7]: b'caf\xc3\xa9'
  
  In [8]: cafe[0]                        
  Out[8]: 99
  
  In [9]: cafe[:1]                               
  Out[9]: b'c'
  
  In [10]: cafe_arr = bytearray(cafe)
  In [11]: cafe_arr                                     
  Out[11]: bytearray(b'caf\xc3\xa9')
  
  In [12]: cafe_arr[-1:]                              
  Out[12]: bytearray(b'\xa9')
  ```

  