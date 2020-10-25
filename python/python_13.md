# python 列表和元组的应用
## 录入学生成绩
```python
names = ["关羽", "张飞", "赵云", "马超", "黄忠"]
courses = ["语文", "数学", "英语"]
scores = [[0] * len(courses) for _ in range(len(names))]

for i, name in enumerate(names):
    print(f"请输入{name}的成绩")
    for j, course in enumerate(courses):
        scores[i][j] = int(input(f"{course}:"))

print()
print('-' * 5, '学生平均成绩', '-' * 5)
for index, name in enumerate(names):
    avg_scores = sum(scores[index]) / len(courses)
    print(f"{name}的平均成绩为{avg_scores:.1f}分")
print()
print('-' * 5, '课程平均成绩', '-' * 5)
for index, course in enumerate(courses):
    # 用生成式从scores中取出指定的列创建新列表
    curr_course_scores = [score[index] for score in scores]
    avg_score = sum(curr_course_scores) / len(names)
    print(f'{course}的平均成绩为：{avg_score:.1f}分')
```
列表生成式`scores = [[0] * len(courses) for _ in range(len(names))]`\
循环嵌套生成`[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]]`

通过enumerate处理后的列表在循环遍历时会取到一个二元组，解包之后第一个值是索引，第二个值是元素。
```python
items = ['Python', 'Java', 'Go', 'Swift']

>>> for index in range(len(items)):
>>>     print(f'{index}: {items[index]}')
0: Python
1: Java
2: Go
3: Swift
>>> for index, item in enumerate(items):
>>>     print(f'{index}: {item}')
0: Python
1: Java
2: Go
3: Swift
```
`curr_course_scores = [score[index] for score in scores]`
列表生成式在`scores`列表中取`score`列表的`index`索引生成列表。

`sum`函数`sum(curr_course_scores)`把一个可以迭代的对象的所有迭代后对象相加。
## 输入日期返回是该年的第多少天
```python
def which_day(year, month, day):
    days = 0
    if year % 400 == 0 or year % 4 ==0 and year % 100 != 0:
        half_year = 182
        month_2 = 29
    else:
        half_year = 181
        month_2 = 28
    if month >= 7:
        days += half_year
        for m in range(7, month):
            if m == 9 or m == 11:
                days += 30
            else:
                days += 31
    else:
        for m in range(1, month):
            if m == 4 or m == 6:
                days += 30
            elif m == 2:
                days += month_2
            else:
                days += 31
    days += day
    return days


print(which_day(1981, 12, 31))  # 365
```

```python
def is_loop_year(year):
    if year % 4 == 0 and year % 100 !=0 or year % 400 ==0:
        return True
    else:
        return False


def which_day(year, month, day):
    date = [[31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31],
            [31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]]

    days = date[is_loop_year(year)]
    total = 0
    for index in range(month - 1):
        total += days[index]

    return total + day


print(which_day(2018, 1, 31))  # 31
```
`days = date[is_loop_year(year)]`因为在python中`True`可以返回\
为1,`False`可以返回为0，所有如果是闰年就使用`date[1]`，是平年就\
使用`date[0]`
## 实现双色球随机选号
```python
from random import randint

Lottery = [0] * 6

for index in range(6):
    Lottery[index] = randint(1, 33)

Lottery.append(randint(1, 16))

print(Lottery)
```
```python
from random import randint, sample


def random_select():
    all_balls = [x for x in range(1, 33)]
    red_balls = sample(all_balls, 6)
    red_balls.sort()
    red_balls.append(randint(1, 16))
    return red_balls


def display(balls):
    for index, ball in enumerate(balls):
        if index == len(balls) - 1:
            print("|", end=" ")
        print(f"{ball:0>2d}", end=" ")
    print()


display(random_select())

```
`print(f"{ball:0>2d}", end=" ") `python格式化`{:0>2d}`表示数字补零 (填充左边, 宽度为2)\
`red_balls = sample(all_balls, 6)`使用`sample`函数在指定的区域中随机取6个数据,使用`sample`是因为在双色球中不能出现重复数字。
## 幸运的女人
```python
persons = [True] * 30
# counter - 扔到海里的人数
# index - 访问列表的索引
# number - 报数的数字
counter, index, number = 0, 0, 0
while counter < 15:
    if persons[index]:
        number += 1
        if number == 9:
            persons[index] = False
            counter += 1
            number = 0
    index += 1
    index %= 30
for person in persons:
    print('女' if person else '男', end='')
```
`if persons[index]: 
        number += 1`保证是数9个活着的人,不会把已经扔到海里面的人算进来。\
`index %= 30`在列表中过了一个循环后,回到列表首项。
在列表中使用`True`和`False`太实用了,一开始设想使用1和0,发现还需要另外加条件判断,过于麻烦。
