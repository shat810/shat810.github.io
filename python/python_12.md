# python 元组
## 元组打包和解包
当我们把多个用逗号分隔的值赋给一个变量时，多个值会打包成一个元组类型；当我们把一个元组赋值给多个变量时，元组会解包成多个值然后分别赋给对应的变量，如下面的代码所示。
```python
# 打包
a = 1, 10, 100
print(type(a), a)    # <class 'tuple'> (1, 10, 100)
# 解包
i, j, k = a
print(i, j, k)       # 1 10 100
```
解包时，如果解包出来的元素个数和变量个数不对应，会引发ValueError异常，错误信息为：too many values to unpack（解包的值太多）或not enough values to unpack（解包的值不足）。\
为了解决个数不对应的问题，我们可以使用星号表达式，有了星号表达式，我们就可以让一个变量接收多个值，用星号表达式修饰的变量会变成一个列表，列表中有0个或多个元素。星号表达式在一次解包的过程中只能出现一次。\
```python
a = 1, 10, 100, 1000
i, j, *k = a
print(i, j, k)          # 1 10 [100, 1000]
i, *j, k = a
print(i, j, k)          # 1 [10, 100] 1000
i, j, k, l, *m = a
print(i, j, k, l, m)    # 1 10 100 1000 []
```
值得注意的是，解包语法对于所有序列都有效，例如字符串，列表以及`range`函数都可以使用解包语法。
```python
>>> a, b, *c = range(1, 10)
>>> print(a, b, c)
1 2 [3, 4, 5, 6, 7, 8, 9]
>>> a, b, c = [1, 10, 100]
>>> print(a, b, c)
1 10 100
>>> a, *b, c = 'hello'
>>> print(a, b, c)
h ['e', 'l', 'l'] o
```
对于函数的可变函数，其实就是把多个参数打包成了一个元组。
```python
def add(*args):
    print(type(args), args)
    total = 0
    for val in args:
        total += val
    return total


add(1, 10, 20)        # <class 'tuple'> (1, 10, 20)
add(1, 2, 3, 4, 5)    # <class 'tuple'> (1, 2, 3, 4, 5)
```
## 元组和列表的相互转换
```python
# 将元组转换成列表
info = ('骆昊', 175, True, '四川成都')
print(list(info))       # ['骆昊', 175, True, '四川成都']
# 将列表转换成元组
fruits = ['apple', 'banana', 'orange']
print(tuple(fruits))    # ('apple', 'banana', 'orange')
```