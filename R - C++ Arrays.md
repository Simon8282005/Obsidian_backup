列表！！！！ C++ 想要创建一个列表和 Python 还是有差别的，C++ 需要在列表名称前面多机上变量的名字：

`string cars[5];` 

大括号里面的数字代表，这个列表能储存多少个 element

`string cars[5] = {"Volvo", "BMW", "Ford", "Mazda", "Toyota"}`

`int numbers[4] = {1, 2, 3, 4, 5}`

# 定位列表里的元素

`cout << cars[0];  // Output = Volvo`

# 更改列表里的元素

`cars[0] = "Mishubishi";`
`cout << cars[0];  // Output = Mishubishi`

# 遍历列表

### For

```c++
int numbers[5] = {1, 2, 3, 4, 5};

for (int i = 0; i < 5; i++) {
	cout << numbers[i] << "\n";
}
```

### Foreach

```c++
int numbers[5] = {1, 2, 3, 4, 5};

for (int i : numbers) {
	cout << numbers[i] << "\n";
}
```

foreach loop 里 i 已经是列表里的元素了，所以不需要在写 `numbers[i]` 了

```c++
int numbers[5] = {1, 2, 3, 4, 5};

for (int i : numbers) {
	cout << i << "\n";
}
```

# Omit array size

其实不一定在在创建列表的时候就决定可以放多少个元素，可以将大括号里面的数字忽略

`string cars[5];  // Specific the size of this array`
`string cars[];  // Didn't specific the size of this array, language will determined the size of this array base on how many elements this array include`

# Size of array

`sizeof(arrayName);`

```c++
int myNumbers[5] = {10, 20, 30, 40, 50};  
cout << sizeof(myNumbers);  // Output = 20....wait what ???
```

shift, C++ 出问题了，5 个元素它竟然说是 20 个，完蛋了完蛋了。。。冷静兄弟 XDD C++没出问题，它只是把列表的大小用 bytes 来表现出来而已啦

还记得 [[I - C++ 数据类型 (Data Type)]] 里提到的吗，int 占用的内存为 4 bytes, 所以 4 * 5 个元素 = 20 byets，没错呀 XDD

那要怎样才能得到一个列表的元素数量呢？我看不懂bytes 勒。。。。

那就除上数据类型所占用的 bytes 大小就好啦 XDD

```c++
int array_length = sizeof(myNumbers) / sizeof(int);  // 20 除以 4 = 5
```

### Size of array in For loop

上面我们使用 for 循环时都是写 `i < 5`, 这其实只能用于某些特定的列表，并且我们是知道列表的总数的

```c++
int numbers[5] = {1, 2, 3, 4, 5, ...};

for (int i = 0; i < sizeof(numbers) / sizeof(int); i++) {
	cout << numbers[i] << "\n";
}
```

方便多了

# # Multi-Dimensional Arrays

[❮ Previous](https://www.w3schools.com/cpp/cpp_arrays_size.asp)[Next ❯](https://www.w3schools.com/cpp/cpp_structs.asp)