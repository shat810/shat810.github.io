# python迭代
如果给定一个list或tuple，我们可以通过for循环来遍历这个list或tuple，这种遍历我们称为迭代（Iteration）。

在Python中，迭代是通过for ... in来完成的，而很多语言比如C语言，迭代list是通过下标完成的，比如Java代码：
```java
for (i=0; i<list.length; i++) {
    n = list[i];
}
```
可以看出，Python的for循环抽象程度要高于C的for循环，因为Python的for循环不仅可以用在list或tuple上，还可以作用在其他可迭代对象上。

list这种数据类型虽然有下标，但很多其他数据类型是没有下标的，但是，只要是可迭代对象，无论有无下标，都可以迭代，比如dict就可以迭代：
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
>>>for i, x in enumerate(l):
...    print(i, x)
0 shat
1 mmj
2 ggbo
```
上面的for循环里，同时引用了两个变量，在Python里是很常见的，比如下面的代码：
```python
>>> for x, y in [(1, 1), (2, 4), (3, 9)]:
...     print(x, y)
1 1
2 4
3 9
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
