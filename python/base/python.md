##  callable 可调用对象

`Callable[[Arg1Type, Arg2Type], ReturnType]` 实现类型提示







## classmethod 类方法

classmethod 不需要实例化，第一个参数不需要时self，但是必须是cls，用于调用实例化参数、实例化属性







## chainmap方法总结

ChainMap 非常强大的dict字典组合功能，他将多个dict字典放入到一个list中，他比dict字典使用update快很多。通过ChainMap可以来模拟嵌套的情景，而且多用于模板之中。





## setattr、getattr 方法

setattr 用于动态设置对象属性，减少代码数量

getattr 用于获取对应的对象属性值等





### inspect 方法 

```python
# inspect 方法可以获取对应的模块中的所有成员，较长用于函数验证
import file_module # 查找对应的

for name , data in inspect.getmembers(file_module):
  print(name)
  print(data)

'''
A : <class 'inspect_total.A'>
B : <class 'inspect_total.B'>
instance_of_a : <inspect_total.A object at 0x10b5aeb80>
module_level_function : <function module_level_function at 0x10b5049d0>


'''


```





### 函数签名

函数签名=参数个数+参数类型+返回值

python 中获取参数的两个方法

- __annotations__

​		返回所有函数中标注的参数

- inspect.signature

  inspect.signature可以创建一个对象，参数为函数对象，它能够捕获关于这个函数的签名信息，就算没有标注也能捕获.

  



## args 、kwargs的区别

*args表示任何多个无名参数，它是一个tuple；**kwargs表示关键字参数，它是一个dict。并且同时使用*args和**kwargs时，必须*args参数列要在**kwargs前，像foo(a=1, b='2', c=3, a', 1, None, )这样调用的话，会提示语法错误



### pd.json_normalize 方法

相较于传统的pd.DataFrame方法，该方法主要是能够将嵌套的json结构进行解析，生成对应的多列数据。

```python
l_nested = [{'name': 'Alice', 'age': 25, 'id': {'x': 2, 'y': 8}},{'name': 'Bob', 'id': {'x': 10, 'y': 4}}]

print(pd.DataFrame(l_nested))
#     name   age                 id
# 0  Alice  25.0   {'x': 2, 'y': 8}
# 1    Bob   NaN  {'x': 10, 'y': 4}

```







### python 中的wraptext

```python
import wraptext
wraptext.fill() #对text中的字符单独换行
wraptext.indent() #将prefix 添加到text 的开头
wraptext.dedent()	#移除每一行开头的相同的的前缀空白符


```









### python中的__slot__使用

```
__slot__ 的使用是为了固定class 中的属性, __slot__ 声明类中包含的属性，若为类中新增属性则会造成keyerror，为定义好的属性预留对应的空间，并加快对应的属性访问时间

```

```
```





### python中的实例方法、类方法、静态方法

- 实例方法

​		第一个参数必须是实例对象，该参数一般约定为"self"，通过他传递对应实例属性和方法

- 类方法

​		使用装饰器@classmethod 进行调用，第一个参数必须要是当前类对象，通过他来传递类是的实例对象和方法。

- 静态方法





### python中的变量的命名

单个`_` 开头的变量、函数、类在使用 `from xx import *`时不会导入

`__`开头的实例属性、方法，会调用名字重整 ` --> _类名__属性名 `

父类中属性名为`__`开头的，子类不继承不能进行访问

如果在子类中定义一个`__`的变量，那么在子类中会生成一个与父类相同名字的属性









