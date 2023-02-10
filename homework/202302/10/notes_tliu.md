# notes

把函数当成 first class 变量的语言都需要考虑这样一个问题：你在一个 scope 里面定义了一个函数，然后在另一个 scope 里面调用这个函数。那么这个时候 free variable 应该怎么取值呢？

Python 的做法是 closure，也就是这个值应该是outer function中的变量的值。
另一种做法是：直接在当下的 environment 中寻找这样一个名字的变量。这样就相当调用这个函数，就真的像是 C++ 中的宏替换一样，一行一行的复制过来然后执行。

这样的问题是：函数的实现理论上不是用户应该关心和看见的，所以我怎么知道这个函数里用到了什么变量呢？还得我自己去先定义好，这显然不太合理。

McCarthy’s paper is a masterpiece as great as Beethoven’s 9th Symphony

Lisp 就是一个 Dynamic Scope 的语言。
Lexical Scope 是说，自由变量在 evaluaed 的时候是按照函数被定义的时候来算的。最早的 Lexical Scope 可能是 Algol。

One notable exception is JavaScript, where the special variable this is confusing because it can be lexically or dynamically scoped, depending on how the code is written.