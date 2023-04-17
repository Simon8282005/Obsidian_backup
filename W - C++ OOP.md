OOP 全称是 Object Oriented Programming （面向对象编程）

### 好处

- 能提升代码的可复用性
- 项目的结构更加的清晰明了

像 Godot 里，我们没吃创建一个新的 Sprite 都会 extend sprite class （godot 已经定义好了的），而 position 和 rotation 就是 sprite 里面的参数

![[Pasted image 20230417104103.png]]

![[Pasted image 20230417104110.png]]

# Classes and Objects

现实世界中，一辆车就是一个 class，而它的 attributes 就是轮胎，引擎等等，它也有自己的 method，像是 drive，stop

使用关键字 **class** 来创建一个 class

```c++
class MyClass {       // The class  
  public:             // 权限
    int myNum;        // Attribute (int variable)  
    string myString;  // Attribute (string variable)  
};
```

![[Pasted image 20230417105428.png]]

```cpp
#include <iostream>
using namespace std;


class computer_class {
public:
    string cpu_type;
    string gpu_type;
    float cpu_hz;
    int ram;
    int rom;
};


void choose_computer (string cpu_type, string gpu_type, float cpu_hz, int ram, int rom) {
    computer_class new_computer;
    new_computer.cpu_type = cpu_type;
    new_computer.gpu_type = gpu_type;
    new_computer.cpu_hz = cpu_hz;
    new_computer.ram = ram;
    new_computer.rom = rom;

    cout << "Cpu type: " << new_computer.cpu_type << "\n";
    cout << "Gpu type: " << new_computer.gpu_type << "\n";
    cout << "Cpu hz: " << new_computer.cpu_hz << "\n";
    cout << "Ram: " << new_computer.ram << "\n";
    cout << "Rom: " << new_computer.rom;
}

int main() {

    choose_computer("Intel i9", "Nvidia 4090 Ti", 4.40, 64, 1000);
    return 0;
}

/*
Output: 

Cpu type: Intel i9
Gpu type: Nvidia 4090 Ti
Cpu hz: 4.4
Ram: 64
Rom: 1000
*/
```

和 Java 一样，class 是一个模板，我们需要用这个模板来定义一个 object

```cpp
conputer_class new_conputer;
```

当然了，还能定义多个实例:

```c++
// Create a Car class with some attributes  
class Car {  
  public:  
    string brand;     
    string model;  
    int year;  
};  
  
int main() {  
  // Create an object of Car  
  Car carObj1;  
  carObj1.brand = "BMW";  
  carObj1.model = "X5";  
  carObj1.year = 1999;  
  
  // Create another object of Car  
  Car carObj2;  
  carObj2.brand = "Ford";  
  carObj2.model = "Mustang";  
  carObj2.year = 1969;  
  
  // Print attribute values  
  cout << carObj1.brand << " " << carObj1.model << " " << carObj1.year << "\n";  
  cout << carObj2.brand << " " << carObj2.model << " " << carObj2.year << "\n";  
  return 0;  
}
```

# Class Methods

method 就是一个 class 里面的 function

在 class 内部定义一个function
```c++
class MyClass {        // The class  
  public:              // Access specifier  
    void myMethod() {  // Method/function defined inside the class  
      cout << "Hello World!";  
    }  
};  
  
int main() {  
  MyClass myObj;     // Create an object of MyClass  
  myObj.myMethod();  // Call the method  
  return 0;  
}
```

在 class 外部定义一个function (需要用到 `::`)
```c++
class MyClass {        // The class  
  public:              // Access specifier  
    void myMethod();   // Method/function declaration  
};  
  
// Method/function definition outside the class  
void MyClass::myMethod() {  
  cout << "Hello World!";  
}  
  
int main() {  
  MyClass myObj;     // Create an object of MyClass  
  myObj.myMethod();  // Call the method  
  return 0;  
}
```

```c++
#include <iostream>
using namespace std;


class computer_class {
public:
    void on();
};

void computer_class::on() {
    cout << "PC starting...";
}

int main() {
    computer_class computer;
    computer.on();
    return 0;
}

/*
Output: PC starting...
*/
```

当然，添加参数也不是不行：
```c++
#include <iostream>  
using namespace std;  
  
class Car {  
  public:  
    int speed(int maxSpeed);  
};  
  
int Car::speed(int maxSpeed) {  
  return maxSpeed;  
}  
  
int main() {  
  Car myObj; // Create an object of Car  
  cout << myObj.speed(200); // Call the method with an argument  
  return 0;  
}  

[Try it Yourself »](https://www.w3schools.com/cpp/trycpp.asp?filename=demo_object_method_param)
```

### 小总结

- 使用 `class` 关键字来创建一个 class
- class 就是车，attributes 就是轮胎，method 几时 drive stop
- class 就像是 template，需要在使用前用这个模板 declare 一个 object `my_template my_obj;`
- 在 class 外面定义function，需要使用 `::`
```c++
class my_class {
public:
	void my_method();
};

void my_class::my_method() {
	...
}
```

明天继续学习 C++ Constructors

