# python 函数和字符串的应用
## 验证码
```python
import random

ALL_CHARS = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'


def generate_code(code_len=4):
    """生成指定长度的验证码
    :param code_len: 验证码的长度(默认4个字符)
    :return: 由大小写英文字母和数字构成的随机验证码字符串
    """
    code = ''
    for _ in range(code_len):
        # 产生0到字符串长度减1范围的随机数作为索引
        index = random.randrange(0, len(ALL_CHARS))
        # 利用索引运算从字符串中取出字符并进行拼接
        code += ALL_CHARS[index]
    return code


for _ in range(10):
    print(generate_code())

```
首先创建一个0-9和26个大小写字母的字符串`ALL_CHARS`，然后创建函数，默认验证码长度为4。\
 在函数中创建验证码字符串code为空，然后在0到`ALL_CHARS`的长度中随机取数，将取到的数字作为索引，把`ALL_CHARS`中的字符加到`code`中去，函数返回字符串`code`。

 ## 返回文件名后缀
 ```python
def get_suffix(filename):
    """获取文件名的后缀名
    :param filename: 文件名
    :return: 文件的后缀名
    """
    # 从字符串中逆向查找.出现的位置
    pos = filename.rfind(".")
    # 通过切片操作从文件名中取出后缀名
    return filename[pos + 1:] if pos > 0 else ""
```
首先创建函数接收文件名，然后将文件名从后面开始查找`.`出现的位置，将数值传给`pos`，通过逆向切片找到`pos + 1`到结尾的文件后缀，值得注意的是因为在`Linux`和`macOS`系统上，文件名可以以`.`开头，表示这是一个隐藏文件，像`.gitignore`这样的文件名，.后面并不是后缀名，这个文件没有后缀名或者说后缀名为`""`。
## 跑马灯
```python
import os
import time

content = '北 京 欢 迎 你 为 你 开 天 辟 地.......'
while True:
    # Windows清除屏幕上的输出
    # os.system('cls')
    # macOS清除屏幕上的输出
    os.system("cls")
    print(content)
    # 休眠0.2秒（200毫秒）
    time.sleep(0.2)
    content = content[1:] + content[0]
```
首先创建一个文本字符串`content`，在末尾加上一些`....`有利于视觉上感受滚动的文本。\
滚动的基础就是把原本字符串的第一项通过切片和字符串拼接移动到字符串末尾，通过每0.2秒打印一次新的字符串和刷新屏幕实现。