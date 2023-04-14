
好家伙，终于接触到了 C++ 的核心功能了，和电脑的记忆体进行通讯

使用 `&` 字符：

```c++
int food = "Pizza";
int &meal = food;

cout << food << "\n";  // Output = Pizza
cout << meal;  // Output = Pizza
```

根据我的理解，`&` 字符让程序从电脑的记忆体里挖出 `food` 变量的数据然后再赋值给 `meal`

这就很好玩有没有 XDD

记忆体是用 hexadecimal form (0x..) 来储存的

```c++
string food = "Pizza";  
  
cout << &food; // Outputs 0x6dfed4
```

# 总结

References 让我们能够操作电脑记忆体里的数据

- 使用 `&` 字符来获得电脑记忆体里的数据的地址并赋值到另外一个变量上
- 由于地址一样，数据自然也就一样了

```c++
string food = "Pizza";
string &meal = food;
cout << meal;  // Output = "Pizza"
```

- `&` 符号只是获得变量的地址，所以如果打印的时候没有带上就表示只想打印数据
- 想查看具体的数据的内存地址就需要在前面加上一个 `&`

- `string &meal = food;` 获取 `food` 的内存地址 (Reference) 并赋值给 `meal`
- `cout << meal;` 打印出 `meal` 的数据


明天将会 focus C++ 最让人抓狂的指针 (pointer)，需要一些时间来理解