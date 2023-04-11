# While 循环

```cpp
while (condition) {
  // code block to be executed
}
```

# Do-while

```cpp
do {
  // code block to be executed
}
while (condition);
```

# For 循环

```cpp
for (statement 1; statement 2; statement 3) {
  // code block to be executed
}
```

For 语句还能进行嵌套呢 XDD

```cpp
// Outer loop
for (int i = 1; i <= 2; ++i) {
  cout << "Outer: " << i << "\\n"; // Executes 2 times

  // Inner loop
  for (int j = 1; j <= 3; ++j) {
    cout << " Inner: " << j << "\\n"; // Executes 6 times (2 * 3)
  }
}
```

### **The foreach Loop**

emm…这是啥呀 XDDD

```cpp
for (type variableName : arrayName) {
  // code block to be executed
}
```

作用是拿来遍历列表（array）或者是其他的数据集

这里有一个例子：

```cpp
int myNumbers[5] = {10, 20, 30, 40, 50};
for (int i : myNumbers) {
  cout << i << "\\n";
}
```

![[Untitled 1.png]]

