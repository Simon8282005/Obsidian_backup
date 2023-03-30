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

# 