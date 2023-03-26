感觉自己还是有东西还没掌握好呢。。。没事，我们慢慢来，先去复习一下基本的概念吧

---

# Lesson 2: Your first Error

别看到错误就心慌，错误对编程来说是好是，起码知道那里要改，如果完全没有错误的话就真的很烦了 XDDD

---

# Lesson 3: We Stand on the Shoulders of Giants (我们站在巨人的肩膀上)

已经有很多人帮我们写好轮子了，我们现在只要用就可以啦 XDDD

![[Pasted image 20230324083701.png]]

在 `rotate()` function 里面使用的数值是 *radian* ，不是 degree

![[Pasted image 20230324083547.png]]

在次看见了熟悉的 formula 呢 XDDD

2 PI = 一个圆圈哦

![[Pasted image 20230324083815.png]]

`move_local_x()` 和 `move_local_y` 是用 pixel 来算的

![[Pasted image 20230324084139.png]]

godot 里坐标的原点是在画面（应该是说一个 sprite）的左上角，向下 y 是 +ve, x 也是 +ve

# Lesson 4: Drawing a Rectangle

![[Pasted image 20230324084757.png]]

你好呀海龟兄 XDD

# Lesson 5: Coding Your First Function

```python
func draw_square:
	move_forward(200)
	turn_right(90)
	move_forward(200)
	turn_right(90)
	move_forward(200)
	turn_right(90)
	move_forward(200)
	turn_right(90)
```

# Lesson 6: Your First Function Parameter

![[Pasted image 20230325145631.png]]

![[Pasted image 20230325150140.png]]

# Lesson 7: Introduction to Member Variable


![[Pasted image 20230325153034.png]]

![[Pasted image 20230325153153.png]]

和数学里的坐标有出入

# Lesson 8: Define Your Own Variables

GDScript里，变量更像是一种标签，让你为这个数据贴上相对应的标签，避免它消失在茫茫"数"海中

# Lesson 9: Adding and Subtracting (减去)

![[Pasted image 20230325154956.png]]

这血条真别致啊 XDDD

# Lesson 10: The Game Loop

![[Pasted image 20230326081526.png]]

有 `_` 的代码，比如 `_process（）` 或是 `_ready()` 代表这个 function 已经被 godot 定义好了

有 `__` 的变量通常代表着不能背直接访问，这个习惯可以提升代码的可读性和可维护性

```python
def __init__(self):
	pass
```

之前学 python 的时候就很奇怪为什么会有两个 `__` ，原来这代表这个函数是强制私有，不能被之间访问

`_process` 每秒的运行速度取决于电脑的运行速度，电脑 cpu 越强，运行次数越多

# Lesson 11: Time Delta (Delta 是啥来着)

> 60 FPS 表示每妙有 60 张图片被更新（像像素画）动画的格式

![[Pasted image 20230326083009.png]]

`delta` 回传 Godot 用了多久的时间来完成上一个 frame

![[Video_2023_03_26-1_edit_0.gif]]

这就是有用 `delta` 和没用 `delta` 的区别，明显有用 `delta` 的运行速度比较快，有了 `delta`， 游戏才能平稳的在各种设备上运行，不会出现配置比较好的电脑游戏会运行比较快的情况


# Lesson 12: Using Variable to Make Code Eaier to Read

![[Pasted image 20230326091435.png]]

在第二行，我们需要猜到底 4 是什么来的究竟是代表什么，但如果使用一个 variable 情况就好多了

![[Pasted image 20230326091626.png]]

看起来清楚多了 (angular = 角度)

![[Pasted image 20230326091852.png]]

定义在 function 里面当然只有这个 function 能用咯