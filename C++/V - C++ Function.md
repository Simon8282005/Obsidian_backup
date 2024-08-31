C++ 里的 function 和 java 里面的基本一致：

```cpp
void myFunction() {
  // code to be executed
}
```

呼叫 function 也和 java 里一致

```cpp
// Create a function
void myFunction() {
  cout << "I just got executed!";
}

int main() {
  myFunction(); // call the function
  return 0;
}

// Outputs "I just got executed!"
```

但是，如果要先 declare 一个 function 然后在写了 main() 之后再定义 fucntion 里面的内容也是可以

这能提升代码可读性

```cpp
// Create a function
void myFunction();

int main() {
  myFunction(); // call the function
  return 0;
}

void myFunction() {
  cout << "I just got executed!";
}
```

# Parameters & arguments

```cpp
void functionName(parameter1, parameter2, parameter3) {
  // code to be executed
}
```

```cpp
void myFunction(string fname) {
  cout << fname << " Refsnes\\n";
}

int main() {
  myFunction("Liam");
  myFunction("Jenny");
  myFunction("Anja");
  return 0;
}

// Liam Refsnes
// Jenny Refsnes
// Anja Refsnes
```

### Default parameter value

```cpp
void myFunction(string country = "Norway") {
  cout << country << "\\n";
}

int main() {
  myFunction("Sweden");
  myFunction("India");
  myFunction();
  myFunction("USA");
  return 0;
}

// Sweden
// India
// Norway
// USA
```

### Multiple parameter

```cpp
void myFunction(string fname, int age) {
  cout << fname << " Refsnes. " << age << " years old. \\n";
}

int main() {
  myFunction("Liam", 3);
  myFunction("Jenny", 14);
  myFunction("Anja", 30);
  return 0;
}

// Liam Refsnes. 3 years old.
// Jenny Refsnes. 14 years old.
// Anja Refsnes. 30 years old.
```

### Return keyword

别忘了 function 是能够回传参数的，但不能使用 void 关键字

```cpp
int myFunction(int x) {
  return 5 + x;
}

int main() {
  cout << myFunction(3);
  return 0;
}

// Outputs 8 (5 + 3)
```

```c
int myFunction(int x, int y) {
  return x + y;
}

int main() {
  cout << myFunction(5, 3);
  return 0;
}

// Outputs 8 (5 + 3)
```

```cpp
int myFunction(int x, int y) {
  return x + y;
}

int main() {
  int z = myFunction(5, 3);
  cout << z;
  return 0;
}
// Outputs 8 (5 + 3)
```

### Pass by reference

```cpp
void swapNums(int &x, int &y) {
  int z = x;
  x = y;
  y = z;
}

int main() {
  int firstNum = 10;
  int secondNum = 20;

  cout << "Before swap: " << "\\n";
  cout << firstNum << secondNum << "\\n";

  // Call the function, which will change the values of firstNum and secondNum
  swapNums(firstNum, secondNum);

  cout << "After swap: " << "\\n";
  cout << firstNum << secondNum << "\\n";

  return 0;
}
// Output:
/*
Before swap: 
1020
After swap: 
2010
*/
```

```cpp
#include <iostream>
using namespace std;

void swapNums(int x, int y) {
  int z = x;
  x = y;
  y = z;
}

int main() {
  int firstNum = 10;
  int secondNum = 20;

  cout << "Before swap: " << "\\n";
  cout << firstNum << secondNum << "\\n";

  swapNums(firstNum, secondNum);

  cout << "After swap: " << "\\n";
  cout << firstNum << secondNum << "\\n";

  return 0;
}
// Output:
/*
Before swap: 
1020
After swap: 
1020
*/
```

### **Pass Array to a Function**

还能回传列表呢，厉害吧 XDD

```cpp
void myFunction(int myNumbers[5]) {
  for (int i = 0; i < 5; i++) {
    cout << myNumbers[i] << "\\n";
  }
}

int main() {
  int myNumbers[5] = {10, 20, 30, 40, 50};
  myFunction(myNumbers);
  return 0;
}
```

# Function Overloading 重载

就算两个函数的名称一样也没有关系，只要类型是不一样的就可以了

```cpp
int my_function = (int x)
float my_function = (float x)
double my_function = (double x, double y)
```

其他语言的 Overloading:

Java

```java
public class Calculator {
    public int add(int x, int y) {
        return x + y;
    }
    
    public double add(double x, double y) {
        return x + y;
    }
    
    public int add(int x, int y, int z) {
        return x + y + z;
    }
}
```

Python

```python
def add(x, y, z=0):
    return x + y + z
    
def add(*args):
    return sum(args)

def add(x, y, *, squared=False):
    if squared:
        return x**2 + y**2
    else:
        return x + y
```

根据上面的理论，我们也能这样写：

```cpp
int plusFunc(int x, int y) {
  return x + y;
}

double plusFunc(double x, double y) {
  return x + y;
}

int main() {
  int myNum1 = plusFunc(8, 5);
  double myNum2 = plusFunc(4.3, 6.26);
  cout << "Int: " << myNum1 << "\\n";
  cout << "Double: " << myNum2;
  return 0;
}
```

# Recursion 递归

<aside> 💡 它指的是在函数或方法内部调用自身来解决问题的方法。

</aside>

<aside> 💡 递归通常适用于问题可以分解为更小的同类问题的情况，每次递归调用都会将问题规模缩小，直到问题被划分为足够小的部分，可以直接求解。

</aside>

```cpp
int sum(int k) {
  if (k > 0) {
    return k + sum(k - 1);
  } else {
    return 0;
  }
}

int main() {
  int result = sum(10);
  cout << result;
  return 0;
}
```

为什么需要回传 k + sum (k-1) 呢

ChatGPT 的解释是：

```cpp
1. 执行条件判断：k>0，满足条件
2. 开始执行函数调用：sum(2)
3. 在sum(2)函数中，会执行以下步骤：
	a. 执行条件判断：k>0，满足条件
	b. 开始执行函数调用：sum(1)
	c. 在sum(1)函数中，会执行以下步骤：
		i. 执行条件判断：k>0，满足条件
		ii. 开始执行函数调用：sum(0)
		iii. 在sum(0)函数中，会执行以下步骤：执行条件判断：k<=0，满足条件返回值为0
		iv. 返回到函数调用：sum(1)v. 计算k + sum(k-1) = 1 + 0 = 1
		vi. 返回值为1
		d. 返回到函数调用：sum(2)
		e. 计算k + sum(k-1) = 2 + 1 = 3
		f. 返回值为3
4. 返回到函数调用：sum(3)
5. 计算k + sum(k-1) = 3 + 3 = 6
6. 返回值为6
```

# 总结

-   能将各种数据传给函数，包括但不限于 Reference 和 Array
-   Overloading：两个函数的名称可以一样，只要数据类型不一样就不会报错
-   Recursion 递归: 通过一个函数调用自身的方法解决问题
    -   上面的例子中通过不停的调用 sum(k - 1) 以获得上一次运算获得的号码并且加上新的一个号码