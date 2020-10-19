# python _9
## 字符串
### 原始字符串
python中的字符串可以r或R开头，这种字符串被称为原始字符串，意思是字符串中的每个字符都是它本来的含义，没有所谓的转义字符。
```python
>>> s1 = r"\"hello, world!\""
>>> s2 = r"\n\\hello, world!\\\n"
>>> print(s1, s2, end='')
\"hello, world!\" \n\\hello, world!\\\n
```
### 字符串的运算
我们可以使用+运算符来实现字符串的拼接，可以使用*运算符来重复一个字符串的内容。
```python
s1 = "hello " * 3
print(s1) # hello hello hello 
s2 = "world"
s1 += s2
print(s1) # hello hello hello world
```
### 字符串比较运算
在python直接使用比较运算符比较字符串，是比较两个字符的对应的编码，因为字符串在计算机的存储的形式也是以二进制存储。\
使用is运算符来比较。两个变量对应的字符串是否在内存中相同的位置（内存地址）
```python
s1 = 'hello world'
s2 = 'hello world'
s3 = s2
# 比较字符串的内容
print(s1 == s2, s2 == s3)    # True True
# 比较字符串的内存地址
print(s1 is s2, s2 is s3)    # False True
```
### 字符串的方法
## 
```python
s1 = 'hello, world!'

# 使用capitalize方法获得字符串首字母大写后的字符串
print(s1.capitalize())   # Hello, world!
# 使用title方法获得字符串每个单词首字母大写后的字符串
print(s1.title())        # Hello, World!
# 使用upper方法获得字符串大写后的字符串
print(s1.upper())        # HELLO, WORLD!

s2 = 'GOODBYE'
# 使用lower方法获得字符串小写后的字符串
print(s2.lower())        # goodbye

# startwith方法检查字符串是否以指定的字符串开头返回布尔值
print(s1.startswith('He'))    # False
print(s1.startswith('hel'))   # True
# endswith方法检查字符串是否以指定的字符串结尾返回布尔值
print(s1.endswith('!'))       # True

s3 = 'abc123456'

# isdigit方法检查字符串是否由数字构成返回布尔值
print(s3.isdigit())    # False
# isalpha方法检查字符串是否以字母构成返回布尔值
print(s3.isalpha())    # False
# isalnum方法检查字符串是否以数字和字母构成返回布尔值
print(s3.isalnum())    # True

s = 'hello good world!'

# 从前向后查找字符o出现的位置(相当于第一次出现)
print(s.find('o'))       # 4
# 从索引为5的位置开始查找字符o出现的位置
print(s.find('o', 5))    # 7
# 从后向前查找字符o出现的位置(相当于最后一次出现)
print(s.rfind('o'))      # 12
```
### 格式化字符串
在Python中，字符串类型可以通过center、ljust、rjust方法做居中、左对齐和右对齐的处理。
```python
s = 'hello, world'

# center方法以宽度20将字符串居中并在两侧填充*
print(s.center(20, '*'))  # ****hello, world****
# rjust方法以宽度20将字符串右对齐并在左侧填充空格
print(s.rjust(20))        #         hello, world
# ljust方法以宽度20将字符串左对齐并在右侧填充~
print(s.ljust(20, '~'))   # hello, world~~~~~~~~
```