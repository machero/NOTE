
# signature
函数签名对象，表示调用函数的方法，即定义了函数的输入输出,简单来说使用签名函数能够返回函数的参数列表、对应的参数类型、返回值等
==python 中的函数签名的获取方法有两种==
- 使用__annotations__，但该方法要求函数中的所有参数必须带类型
- 使用inspect 中的signature 方法

```python
# method1: __annotations__
def hello(greet : str,flag):
    print("hello", greet)
print(hello.__annotations__())

# method2: inspect.signature
from inspect import signature 

def foo(value):
    return value

foo_sig = signature(foo)
foo_params = foo_sig.parameters

# 使用 bind 方法传入参数检查对应的参数是否符合函数定义的要求,使用apply_defaults方法进行参数赋值

```


# Threading 中的Thread Local Storage（线程局部存储）




# 什么是接口幂等
从数据式上面来说，一个f(x)经过多次的运算需要保证多次运算和一次运算的结果是一致的。即第一次请求的时候对资源产生了副作用，但是以后的多次请求都不会再对资源产生副作用。
 - 使用乐观锁，在变量通信的过程中设置version版本，多次操作如果id 对应不一致则会导致操作失败，以此来保证接口的幂等性
 - 使用分布式锁，该过程需要构建全局锁的索引，较为麻烦。该过程中一般使用中间系统(zookeeper、redias)获取分布式锁。即同一个时间点该流程只有一个能够执行。




# python 中忽略异常的方法
- 使用try catch 直接进行捕获
- contextlib.suppress() 更加明确的抑制异常在with 块出现的任何地方。




