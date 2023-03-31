吼吼 XDDD 每一个编程语言几乎肯定一定异常确定会有这个呢 XDD

那就先写出来有多少种变量类型吧

`int` - Integer (整数)
`float` & `double` - 小数 (`float` 使用的内存比 `double` 小)
`bool` - Boolean (布尔值，`true` or `false`)
`string` - 句子
`char` - 单个字母

# 定义变量

记得记得，C++ 和 Java 定义变量之前都需要加上关键字，python 和 GDScript 则不需要 (gdscript 要加上 `var` 而已)

### Int

```c
int number = 10;
cout << number;
```

### String

```c
int my_age = 25;
cout << "I am" << my_age << "years old.";
```

![[Pasted image 20230331074841.png]]

---

# 定义多行变量

Python 里是能这样子写的，但在 C++ 里写法就稍微变了一些

```python
x = y = z = 2
```

代码会稍微长那么一点点

```c
int x =2, y = 2, z = 2
// 或者
int x, y, z
x = y = z = 2  // 这样就就可以，但是始终都要先定义变量
```

---

# 独特的名字

每一个变量的名字应该都是唯一的，并且尽量避免单个字母的变量，因为不知道代表着什么

---

# 固执的变量

如果不想改这个变量的数值，就用 `const`  XDDD Java 里面是 `final` 呢，but GDScript 里好像也是 `const`，但并不需要 `const var number = ...` 而是直接用 `const` 来代替 `var`，`const PI = 3.14159`

但 C++ 就不能了

```c
const int pi = 3.14159
```

如果还是想要强行为有 `const` 关键字的变量赋值，compiler 会直接丢出一个 error XDD

![[Pasted image 20230331075855.png]]

![[Pasted image 20230331080027.png]]

