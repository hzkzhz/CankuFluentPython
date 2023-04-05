with 语句会设置一个临时的上下文，交给上下文管理器对象控制，并且负责清理上下文。这么做能避免错误并减少样板代码，因此 API 更安全，而且更易于使用。

这个语言特性不是什么秘密，但却没有得到重视：else 子句不仅能在 if 语句中使用，还能在 for、while 和 try 语句中使用。
for/else、while/else 和 try/else 的语义关系紧密，不过与 if/else 差别很大。

for
仅当 for 循环运行完毕时（即 for 循环没有被 break 语句中止）才运行 else 块。
while
仅当 while 循环因为条件为假值而退出时（即 while 循环没有被 break 语句中止）才运行 else 块。
try
仅当 try 块中没有异常抛出时才运行 else 块。官方文档（https://docs.python.org/3/reference/compound_stmts.html）还指出：“else 子句抛出的异常不会由前面的 except 子句处理。”

在所有情况下，如果异常或者 return、break 或 continue 语句导致控制权跳到了复合语句
的主块之外，else 子句也会被跳过。
