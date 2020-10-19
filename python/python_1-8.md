# python _1-8
## _字符
`_`单个独立下划线是用作一个名字，来表示某个变量是临时的或无关紧要的。\
除了用作临时变量之外，“_”是大多数Python REPL中的一个特殊变量，它表示由解释器评估的最近一个表达式的结果。
```python
>>> 20 + 3
23
>>> _
23
>>> print(_)
23

>>> list()
[]
>>> _.append(1)
>>> _.append(2)
>>> _.append(3)
>>> _
[1, 2, 3]
```
## end参数
Python的print（）函数带有一个名为“ end”的参数。默认情况下，此参数的值为'\ n'，即换行符。您可以使用此参数以任何字符/字符串结束打印语句。end=' '意思是末尾不换行，加空格。
## random
`random.randint(a, b)`
返回随机整数 N 满足 a <= N <= b。相当于 randrange(a, b+1)。
## 斐波那契数
```python
a = 0
b = 1
for _ in range(20):
    a, b = b, a + b
    print(a, end=' ')
```
## 正整数的反转
```python
num = int(input('num = '))
reversed_num = 0
while num > 0:
    reversed_num = reversed_num * 10 + num % 10
    num //= 10
print(reversed_num)
```
## 百钱百鸡
```python
for x in range(0, 20):
    for y in range(0, 33):
        z = 100 - x - y
        if 5 * x + 3 * y + z / 3 == 100:
            print('公鸡: %d只, 母鸡: %d只, 小鸡: %d只' % (x, y, z))
```
## 1000以内的完美数
```python
from math import sqrt
for num in range(1, 10000):
    result = 0
    for factor in range(1, int(sqrt(num)) + 1):
        if num % factor == 0:
            result += factor
            if factor > 1:
                result += num // factor
    if result == num:
        print("%d是一个完美数" % num)
```
## 输出100以内所有的素数
```python
from math import sqrt
for num in range(2, 100):
    is_prime = True
    for factor in range(2, int(sqrt(num)) + 1):
        if num % factor == 0:
            is_prime = False
            break
    if is_prime:
        print(num, end=" ")
```
## 函数参数 
```python
# 在参数名前面的*表示args是一个可变参数
def add(*args):
    total = 0
    for val in args:
        total += val
    return total


# 在调用add函数时可以传入0个或多个参数
print(add())
print(add(1))
print(add(1, 2))
print(add(1, 2, 3))
print(add(1, 3, 5, 7, 9))
```
## 函数入口
一个 Python 源码文件除了可以被直接运行外，还可以作为模块（也就是库）被导入。不管是导入还是直接运行，最顶层的代码都会被运行（Python 用缩进来区分代码层次）。而实际上在导入的时候，有一部分代码我们是不希望被运行的。
## 
```python
# __name__是Python中一个隐含的变量它代表了模块的名字
# 只有被Python解释器直接执行的模块的名字才是__main__
if __name__ == '__main__':
    print('call foo()')
    foo()
    print('call bar()')
    bar()
```
`if __name__ == '__main__'` 我们简单的理解就是： 如果模块是被直接运行的，则代码块被运行，如果模块是被导入的，则代码块不被运行。

`test.py`
```python
import module1 as m1
import module2 as m2

m1.foo()
m2.foo()
```
`as`后导入的名称可以明确到底要使用`foo`函数
## 特殊赋值语句
### 赋值语句中的if
请看下面的代码示例：
```python
>>> a = 123 if True else 321
>>> a
123
>>> a = 123 if False else 321
>>> a
321
```
以上代码，给变量a赋值，如果if True，a的取值就是if前面的那个值，如果if False，a的取值就是else后面的值。
## 赋值语句中的and和or
```python
>>> a = 10 or 20
>>> a
10
>>> a = 10 and 20
>>> a
20
>>> b = 0 or 1
>>> b
1
>>> b = 0 and 1
>>> b
0
```
这种语法在python中叫“短路运算符”，属于python的布尔操作。下面总结一下赋值语句中and和or的语法规则：

表达式从左至右运算，若 or 的左侧逻辑值为 True ，则短路 or 后所有的表达式（不管是 and 还是 or），直接输出 or 左侧表达式 。\
表达式从左至右运算，若 and 的左侧逻辑值为 False ，则短路其后所有 and 表达式，直到有 or 出现，输出 and 左侧表达式到 or 的左侧，参与接下来的逻辑运算。
## 类似三元赋值
```python
>>> a = (1,2)[True]
>>> a
2
>>> a = (1,2)[False]
>>> a
1
>>>
>>> x = 1
>>> a = ("abc", "123")[x == 1]
>>> a
123
>>> a = ("abc", "123")[x != 1]
>>> a
abc
>>> a = ["abc", "123"][x != 1]
>>> a
abc
```