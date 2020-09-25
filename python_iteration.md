# python迭代
在python中迭代是用 `for... in`来完成的,不同于c语言之类的语言迭代的对象都有下标，python迭代的抽象程度更加深，可以用于更多的类型。

可以对dict进行迭代
```python
>>>d = {"shat" : 123, "mmj" : 456, "ggbo" : 789}
>>>for x in d:
...   print(x)
shat
mmj
ggbo
```
如果想要迭代dict的value的话。
```python
>>>d = {"shat" : 123, "mmj" : 456, "ggbo" : 789}
>>>for x in d.value():
...    print(x)
123
456
789
```
同时字符串也是可以迭代的对象。
```python
>>>str = "shat"
>>>for x in str:
...    print(x)
s
h
a
t
```
如果想要list像c语言一样通过下标来迭代的话，python提供了一种`enumerate`函数可以把list变成索引-值的形式。
```python
>>>l = ["shat","mmj","ggbo"]
>>>for x in enumerate(l):
...    print(x)
0 shat
1 mmj
2 ggbo
```
如果不确定能不能迭代的话,判断方法是通过collections模块的Iterable类型
```python
from collections import Iterable
>>> isinstance('abc', Iterable) # str是否可迭代
True
>>> isinstance([1,2,3], Iterable) # list是否可迭代
True
>>> isinstance(123, Iterable) # 整数是否可迭代
False
```