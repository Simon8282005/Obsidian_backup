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

---

# Lesson 13: Coditions （条件）

如果没有条件的话就有出现这种情况了 XDDD

![[Pasted image 20230325154956.png]]

![[Pasted image 20230327084135.png]]

---

# Lesson 14: Multiplying (乘法)

正常的情况来说玩家的 `max_health` 是直线型上升的，但根据大多数游戏的设定，等级越高就需要更多的经验值来升级，所以 `max_health` 的增加当然也不能和之前的较低的等级一样

![[Pasted image 20230327084922.png]]

应该是以这种方式上升

![[Pasted image 20230327085106.png]]

能用 simbol `*=` 让数值直接乘上去

![[Pasted image 20230327085229.png]]

```python
var level = 3
var health = 100
var max_health = 100

func take_damage(amount):
	if level > 2:
		amount *= 0.5

	health -= amount

	if health > max_health:
		health = max_health

	if health < 0:
		health = 0
```

这样写是错误的(在这个例子里面啦)：
```python
...
health -= (amount *= 0.5*)
```

因为有更好的解决办法，就是把 amount `*=.0.5` 就好了

---
# Lesson 15: Modulo (% 余数)

> modulo 不能用在小数点上

这张图能更好的理解 modulo 是怎么一回事

![[Pasted image 20230327113845.png]]

modulo 同样不能和 0 一起搭配，会有错误

![[Pasted image 20230327113946.png]]

### 用处 1：Number Cycle （数字循环）

modulo 能拿来制作一个循环呀（不是 `for` & `while` 的那个循环

![[Pasted image 20230327114232.png]]
![[Pasted image 20230327114243.png]]
![[Pasted image 20230327114306.png]]
![[Pasted image 20230327114317.png]]

```python
1 % 3 = 3
2 % 3 = 1
3 % 3 = 0
```

![[Pasted image 20230327114451.png]]
![[Pasted image 20230327114502.png]]
![[Pasted image 20230327114515.png]]

有图片看就是好多了，1 不能被 3 整除，余 1，2 也一样，所以余 2，但 3 能被整除，余 0，`light_index` 数值又回到了 0，这样就能继续循环下去，不会出现说 `light_index` = 100 这种情况

当然，用 `if` `else` 也可以实现同样的效果，但用 `modulo %` 能写出更简短的代码

![[Pasted image 20230327114906.png]]

### 用处 2：Find even or odd number (单数还是复数)

![[Pasted image 20230327115312.png]]

同理，1 % 2，1 不能被整除，返回 1

反之，2,4,6 都能被 2 整除，返回 0

### 用处 3：Calculating random number within a range

`randi()` function 能生成很多很多很多的号码。。。(10^18 的号码 for 电脑，and 2 billion for 手机)

`modulo %` 就能用来限制随机的数字避免过大

```javascript
func roll_dice():
	var dice_value = randi() % max_number + 1
	display_value(dice_value)
```

1.  当 `randi()` 函数返回0时，计算如下：  
    dice_value = 0 % 6 + 1  
    dice_value = 1
 > 在最后尾端需要加一就是为了避免的到的结果为 0

2.  当 `randi()` 函数返回3时，计算如下：  
    dice_value = 3 % 6 + 1  
    dice_value = 4
    

3.  当 `randi()` 函数返回5时，计算如下：  
    dice_value = 5 % 6 + 1  
    dice_value = 6

跟着顺序跑，先做 % 在做 + 1

### Practice

```javascript
func level_up():
	level += 1
	if level % 2 == 0:
		max_health += 10
	else:
		max_health += 5
```

上面的代码是没有问题，但还能写的更加的简短，逻辑上是一样的 XDD

```javascript
func level_up():
	level += 1
	max_health += 5
	if level % 2 == 0:
		max_health += 5
```


# Lesson 16: 2D Vectors

什么是 vectors ？

> Vectors 是有长度和方向的单位

![[Pasted image 20230328090505.png]]

godot 里，`position.x` 和 `position.y` 的数值是小数点来的，不能直接加 integer

![[Pasted image 20230328092035.png]]

`Vecotr2(x, y)`

# Lesson 17: While Loop

Godot 里貌似没有什么很复杂的循环，比较多看到的是 For 和 While 循环

```javascript
var i = 0
while i < 4:
	print(i)
	i += 1
```

`while` loop 很好用，但要是忘了停止的话那可就完蛋了，它会一直循环一直循环下去知道电脑爆掉

其实 `while` loop 也可以这样写，不一定需要多定义一个变量

```python
while cell.y < board_size.y - 1:
	cell.y += 1
```

上面这种写法会比较简单和简洁一些

```python
var i = 0
while i < 5:
	i += 1
```

### While loop 什么时候要用？？

那么既然 `while` loop 会导致电脑当机，为什么还要用呢？不是还要更安全的 `for` loop 吗？

emm...`while` loop 的用处就是当我们不知道我们要运行这几行代码多少次的时候使用，毕竟用 `for` 时需要指定循环的次数呀

这些是 `while` 的用处：

![[Pasted image 20230328113302.png]]

# Lesson 17: For loop

以前 form 3 上 ask 时，我们同学和老师还有我自己都对 `for` 和 `while` 的差别进行了激烈的讨论，但越讨论越乱 XDDD

现在以我的理解是，`for` 是有指定循环多少次的，但 `while` 是没有指定的，`while` 比较像是当条件不被满足了之后才停止，该条件不一定是要一个变量等于多少多少

![[Pasted image 20230328114229.png]]

```python
for i in range(10):
	print(i)
```

