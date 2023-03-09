# 669~682 Generator - 生成器与简单携程
 - 协程通过使用 yield 暂停生成器，可以将程序的执行流程交给其他的子程序，从而实现不同子程序的之间的交替执行。向暂停的生成器发送信息通常使用it.send(xxx)接口。
 ```python3
 def jumping_range(N):
    index = 0
    while index < N:
        # 通过send()发送的信息将赋值给jump
        jump = yield index
        if jump is None:
            jump = 1
        index += jump

if __name__ == '__main__':
    itr = jumping_range(5)
    print(next(itr))
    print(itr.send(2))
    print(next(itr))
    print(itr.send(-1))
 # 依次输出0 2 3 2
 # yield index 是将index return给外部调用程序。
 # jump = yield 可以接收外部程序通过send()发送的信息，并赋值给jump
 
 ```
