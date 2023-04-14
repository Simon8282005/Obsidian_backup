指针是个很很很特殊的变量，**储存了计算机的记忆体中的某个地址**，那个地址可能包含一些数据或是其他的变量

- 可以实现函数间的数据传递
- 可以动态地分配内存空间

### 可以实现函数间的数据传递

指针在原有内存的地址上进行修改进而可以改变原本变量的值

### 可以动态地分配内存空间

在运行时自动分配和释放内存，不需要在编译时就确定内存大小

在数据类型的关键字后面添加 `*` 来创建指针

```c++
string food = "Pizza";
string* ptr = &food;

// Output the value of food (Pizza)
cout << food;

// Output the memory address of food (0x6dfed4)
cout << &food;

// Output the memory address of food with the pointer (0x6dfed4)
cout << ptr;
```

emm 看得出来，确实是内存的地址呢

#### 指针的数据类型必须要和你想要存储内存地址的变量一样

# Dereference 我就是不要参考 XDD

```c++
string food = "Pizza";
string* ptr = &food;

// Output the memory address of food with the pointer (0x6dfed4)
cout << ptr;
```

这里打印出来的结果是内存的地址，但要是我只要数据而已呢？那就在打印的变量前加上 `**`

```c++
string food = "Pizza";
string* ptr = &food;

// Output = Pizza
cout << *ptr;
```

# 总结

- `&` 符号用来获取电脑的记忆体中的数据
- `*` 用来创建一个名为指针的变量，用来储存获取的数据的内存地址 (必须附上 `&` 已获得该数据的内存地址)
- 用在 declare 变量时，是*创建指针*，反之则是*dereference*

- `string* ptr = &food;` 创建指针
- `cout << *ptr << "\n";` dereference