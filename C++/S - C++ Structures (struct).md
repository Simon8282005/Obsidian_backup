`struct` 能把很多变量集中起来，和列表不一样的是，struct 可以同一时间拥有很多不同类型的变量

# Create a Structure

用 `struct` 关键字来创建 structure 

```c++
struct {             // Structure declaration  
  int myNum;         // Member (int variable)  
  string myString;   // Member (string variable)  
} myStructure;       // Structure variable
```

# Access Structure Members

使用 `.` 定位 struct 里面的变量

```c++
// Create a structure variable called myStructure  
struct {  
  int myNum;  
  string myString;  
} myStructure;  
  
// Assign values to members of myStructure  
myStructure.myNum = 1;  
myStructure.myString = "Hello World!";  
  
// Print members of myStructure  
cout << myStructure.myNum << "\n";  
cout << myStructure.myString << "\n";
```


# One Structure in Multiple Variables

使用 `,` 来在同一行添加多个变量

```c++
struct {  
  int myNum;  
  string myString;  
} myStruct1, myStruct2, myStruct3; // Multiple structure variables separated with commas
```

这样写会有错误的呢，而且 struct 的代码块要在 `int main()` 的外面

![[Pasted image 20230413080536.png]]

这样才是正确的

```c++
#include <iostream>
using namespace std;

struct {
    string band;
    string model;
    int year;
} car_1, car_2;

int main() {
    //Car 1
    car_1.band = "BMW";
    car_1.model = "X8";
    car_1.year = 1999;

    // Car 2
    car_2.band = "Ford";
    car_2.model = "Mustang";
    car_2.year = 1969;

    cout << car_1.band << " " << car_1.model << " " << car_1.year << "\n";
    cout << car_2.band << " " << car_2.model << " " << car_2.year << "\n";

    return 0;
}
```

![[Pasted image 20230413080749.png]]

# Named Structures

```c++
struct myDataType { // This structure is named "myDataType"  
  int myNum;  
  string myString;  
};
```

上面的例子中我以身犯险，放在 `struct` 关键字的后面只能有一个名字，如果要很多个名字需要放在最后一行

那如果我不要放在最后一行，那要怎么写啊

就像这样咯

```c++
// Declare a structure named "car"  
struct car {  
  string brand;  
  string model;  
  int year;  
};  
  
int main() {  
  // Create a car structure and store it in myCar1;  
  car myCar1;  
  myCar1.brand = "BMW";  
  myCar1.model = "X5";  
  myCar1.year = 1999;  
  
  // Create another car structure and store it in myCar2;  
  car myCar2;  
  myCar2.brand = "Ford";  
  myCar2.model = "Mustang";  
  myCar2.year = 1969;  
   
  // Print the structure members  
  cout << myCar1.brand << " " << myCar1.model << " " << myCar1.year << "\n";  
  cout << myCar2.brand << " " << myCar2.model << " " << myCar2.year << "\n";  
   
  return 0;  
}
```

哦哦我明白了，如果是放在最后一行就相当于 declare 这个 struct 时就顺便也创建了变量

相当于上面这个例子中的 `car myCar1;`

# 总结

- `struct` 由不同种类的变量组合而成，帮助我们更容易的定位变量，也为后面的**面向对象**编程提供比那里
- 使用 `.` 来定位 `struct` 里面的变量
- 使用 `,` 来创建多个 `struct` 类型的变量
- 想同时创建多个 `struct` 类型的变量需要放在最后一行

```c++
struct {
	...
} car_1, car_2;
```

- 等同于 

```c++
struct car {
	...
};
```

`car car_1;`
