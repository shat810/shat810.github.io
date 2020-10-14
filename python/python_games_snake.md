# Python Snake
## 原始代码分析
```python
from turtle import *
from random import randrange
from freegames import square, vector

food = vector(0, 0)
snake = [vector(10, 0)]
aim = vector(0, -10)
```
请想象绘图区有一只机器海龟，起始位置在 x-y 平面的 (0, 0) 点。先执行`from turtle import *`，再执行`turtle.forward(15)`，它将(在屏幕上)朝所面对的 x 轴正方向前进 15 像素，随着它的移动画出一条线段。再执行`turtle.right(25)`，它将原地右转 25 度。

`vector(x, y)`向量，两个参数分别是x轴和y轴的坐标。
```python
>>> v = vector(1, 2)
>>> v.x
1
>>> v.y
2
```
```python
def change(x, y):
    "Change snake direction."
    aim.x = x
    aim.y = y

def inside(head):
    "Return True if head inside boundaries."
    return -200 < head.x < 190 and -200 < head.y < 190

def move():
    "Move snake forward one segment."
    head = snake[-1].copy()
    head.move(aim)
```
`head.move()`是用于向量的移动函数，具体规则如下：
```python
>>> v = vector(1, 2)
>>> w = vector(3, 4)
>>> v.move(w)
>>> v
vector(4, 6)
>>> v.move(3)
>>> v
vector(7, 9)
```
```python
    if not inside(head) or head in snake:
        square(head.x, head.y, 9, 'red')
        update()
        return
```
`square(x, y, size, name)`在（x，y）处绘制带有边长为size的正方形并填充颜色name。
```python
    snake.append(head)

    if head == food:
        print('Snake:', len(snake))
        food.x = randrange(-15, 15) * 10
        food.y = randrange(-15, 15) * 10
    else:
        snake.pop(0)
```
如果吃到食物就在`randrange(-15, 15) * 10`的范围中生成随机的x，y轴坐标。\
`snake.pop(0)`如果没有吃到食物的话，就把snake的**索引0**删除，删除索引0
```python
    clear()

    for body in snake:
        square(body.x, body.y, 9, 'black')
```
`clean()`是`turtle`模块中的一个函数，功能是把所有turtle的绘图全部删除。\
`for body in snake:
        square(body.x, body.y, 9, 'black')`在snake中每一个body块都变成黑色，吃掉了n个食物，就有n+1个黑色body块。
```python
    square(food.x, food.y, 9, 'green')
    update()
    ontimer(move, 100)
```
`update()`执行一次屏幕的刷新。\
`ontimer(move, 100)`每间隔100毫秒就调用`一个move()`函数，用于刷新snake的移动路径。
```python
setup(420, 420, 370, 0)
hideturtle()
tracer(False)
listen()
onkey(lambda: change(10, 0), 'Right')
onkey(lambda: change(-10, 0), 'Left')
onkey(lambda: change(0, 10), 'Up')
onkey(lambda: change(0, -10), 'Down')
move()
done()
```
`setup(width, height, startx, starty)`设置主窗口的大小和位置。\
width -- 如为一个整型数值，表示大小为多少像素，如为一个浮点数值，则表示屏幕的占比；默认为屏幕的 50%。

height -- 如为一个整型数值，表示高度为多少像素，如为一个浮点数值，则表示屏幕的占比；默认为屏幕的 75%。

startx -- 如为正值，表示初始位置距离屏幕左边缘多少像素，负值表示距离右边缘，None 表示窗口水平居中。

starty -- 如为正值，表示初始位置距离屏幕上边缘多少像素，负值表示距离下边缘，None 表示窗口垂直居中。

`hideturtle()`隐藏箭头。

`tracer(False)`这个方法是直接展示给用户绘制结果，无需漫长的等待绘制过程。

`listen()`设置焦点到 TurtleScreen ,以便接收按键事件。

`onkey(fun, key)`绑定 fun 指定的函数到按键释放事件。\
`onkey(lambda: change(0, -10), 'Down')`使用`lambda`匿名函数把有参数的函数转换为无参函数，以便于作为`onkey ()`参数转递。

`done()`开始事件循环，调用 Tkinter 的 mainloop 函数。必须作为一个海龟绘图程序的结束语句。
## 功能构想
### 跑出边界
#### 实现方法
```python
    if not inside(head):
        # Make snake go around the edges.
        if head.x == 200 or head.x == -200:
            head.x = -head.x
        elif head.y == 200 or head.y == -200:
            head.y = -head.y
```
每当贪吃蛇触碰到一边的边界时，将它的坐标转化为相应的轴上的负坐标。
### 食物移动
#### 代码
```python
def foodMove():
    food.x = randrange(-15, 15) * 10
    food.y = randrange(-15, 15) * 10
    ontimer(foodMove, 3000)


if head == food:
    print('Snake:', len(snake))
     foodMove()
else:
    snake.pop(0)

foodMove()
```
## BUG
### 改变snake大小
改变snake大小，导致无法随意吃到食物。
#### 解决办法
因为代码吃到食物的逻辑是x，y的坐标完全匹配，所以必须用改变后的模块的左下角去匹配食物。
### 食物移动
```python
    if head == food:
        print('Snake:', len(snake))
        foodMove()
    else:
        snake.pop(0)
```
短时间内连续移动多次。，因为外部的`foodMove()`函数每过三秒就会调用一次，如果吃掉食物的话，三秒后的调用不会停止，导致吃掉食物后，食物立刻转换位置，在三秒之内就会移动到下一个位置，类似于递归函数，导致后期，食物吃的越多，食物转换位置的速度越快。