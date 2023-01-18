# Deep and Shallow Copies of Arbitrary Objects 
- copy(): shallow copy, different id, same content, if the other object update the content, it also changes.
- deepcopy(): deep copy, different id, completely independent from the previous data.

# Function Parameters as References
the parameters inside the function become aliases of the actual arguments.

# Mutable Types as Parameter Defaults: Bad Idea
最好把不可修改的数据做参数，否则，很容易出现修改输入变量的情况。
