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

```cpp
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

# Constructors

好家伙，能够直接创建然后被直接呼叫的啊

```c++
class MyClass {     // The class  
  public:           // Access specifier  
    MyClass() {     // Constructor  
      cout << "Hello World!";  
    }  
};  
  
int main() {  
  MyClass myObj;    // Create an object of MyClass (this will call the constructor)  
  return 0;  
}
```

constructors 的特性基本上是和 function 一致的 [[V - C++ Function]] 

也能设定 Parameter
```c++
class Car {        // The class  
  public:          // Access specifier  
    string brand;  // Attribute  
    string model;  // Attribute  
    int year;      // Attribute  
    Car(string x, string y, int z) { // Constructor with parameters  
      brand = x;  
      model = y;  
      year = z;  
    }  
};  
  
int main() {  
  // Create Car objects and call the constructor with different values  
  Car carObj1("BMW", "X5", 1999);  
  Car carObj2("Ford", "Mustang", 1969);  
  
  // Print values  
  cout << carObj1.brand << " " << carObj1.model << " " << carObj1.year << "\n";  
  cout << carObj2.brand << " " << carObj2.model << " " << carObj2.year << "\n";  
  return 0;  
}
```

也能在 Class 的外面定义，但是记得要用 `::` 符号

```c++
class Car {        // The class  
  public:          // Access specifier  
    string brand;  // Attribute  
    string model;  // Attribute  
    int year;      // Attribute  
    Car(string x, string y, int z); // Constructor declaration  
};  
  
// Constructor definition outside the class  
Car::Car(string x, string y, int z) {  
  brand = x;  
  model = y;  
  year = z;  
}  
  
int main() {  
  // Create Car objects and call the constructor with different values  
  Car carObj1("BMW", "X5", 1999);  
  Car carObj2("Ford", "Mustang", 1969);  
  
  // Print values  
  cout << carObj1.brand << " " << carObj1.model << " " << carObj1.year << "\n";  
  cout << carObj2.brand << " " << carObj2.model << " " << carObj2.year << "\n";  
  return 0;  
}
```

# Access Specifiers 权限

```c++
class MyClass {  // The class  
	public:        // Access specifier  
    // class members goes here  
};
```

一共有三种权限：
- `public` - 能被 class 以外和以内的成员访问 （不管有没有继承同一个 class）
- `private` - 只能被同个class 的成员访问
- `protected` - 能从内部访问，也能被类的派生类 （后面会学到）访问

```c++
class MyClass {  
public:    // Public access specifier  
    int x;   // Public attribute  
private:   // Private access specifier  
    int y;   // Private attribute  
};  
  
int main() {  
  MyClass myObj;  
  myObj.x = 25;  // Allowed (public)  
  myObj.y = 50;  // Not allowed (private)  
  return 0;  
}

// Output: error: y is private
```

默认情况下，如果我们没有指定任何一个权限，那么变量的全都都会是 private

```c++
class MyClass {  
  int x;   // Private attribute  
  int y;   // Private attribute  
};
```

# Encapsulation 封装

这么做的目的是为了避免敏感的数据能直接被随意修改，全部的变量都应该被定义为 private，定义 settler 和 getter 如果需要更改变量

setter getter。。。hello 我们又见面了

```c++
#include <iostream>
using namespace std;


class Employee {
private:
    int salary;
public:
    void set_salary(int x) {
        salary = x;
    }

    int get_salary() {
        return salary;
    }
};


int main() {
    Employee boss;
    boss.set_salary(10000);
    cout << "Salary: " << boss.get_salary();
    return 0;
}

```

Output:

![[Pasted image 20230418083419.png]]

### 小总结

- class 是能直接在内部呼叫自身的
- 呼叫自身和 function 的使用方法一样，也能设置 parameters，也能在 class 外面定义 （记得用 `::` 符号）
```c++
class MyClass {     // The class  
  public:           // Access specifier  
    MyClass() {     // Constructor  
      cout << "Hello World!";  
    }  
};  
  
int main() {  
  MyClass myObj;    // Create an object of MyClass (this will call the constructor)  
  return 0;  
}
```
- 一共有三种权限，`public`, `private`, `protected`
- `public` - 能从类的外部和内部访问
- `private` - 只能从类的内部访问
- `protected` - 能被类的内部访问，也能被继承该类的文件使用
- 封装是为了避免敏感的数据被随意篡改
- 在封装过程中，全部的数据都背设定为 private，并且编写 setter 和 getter 来取得或是更改变量的值

明天继续学 **继承**

# Inheritance

原来 Inheritance 是继承啊。。。java 里是要用 `extends` 关键字的

```java
// 父类(Animal):  
public class Animal {  
	public void makeSound() {  
		System.out.println("Animal sound");  
	}  
}

// 子类(Dog):继承Animal类:  
public class Dog extends Animal {  
	public void makeSound() {  
		System.out.println("Woof! Woof!");  
	}  
}

// 子类(Cat):继承Animal类:  
public class Cat extends Animal {  
	public void makeSound() {  
		System.out.println("Meow!");  
	}  
}

public class Demo {  
	public static void main(String[] args) {  
		Animal a;  
		Dog d = new Dog();  
		Cat c = new Cat();
		a = d;  
		a.makeSound(); // prints "Woof! Woof!"  
		
		a = c;  
		a.makeSound(); // prints "Meow!"  
	}  
}
```

C++ 里，使用 `:` 来继承 class

```c++
#include <iostream>
using namespace std;

class Vehicle {
    public:
    string brand = "Ford";
     void hond() {
        cout << "Tut tut\n";
     }
};

class Car: public Vehicle {
    public:
        string model = "Mustang";
};

int main() {
    Car car;
    car.hond();
    cout << car.brand << " " << car.model;
    return 0;
}
```

![[Pasted image 20230419084113.png]]

就和 Godot 里很像，继承了一个类就可以使用那个类的 method 和更改变量

## Multilevel Inheritance 多层继承

除了被儿子继承，还能被孙子继承 XDD

```c++
#include <iostream>
using namespace std;

class MyClass {
    public:
     void myMethod() {
        cout << "Hello\n";
     }
};

class MyChild: public MyClass {};

class MyGrandChild: public MyClass {};

int main() {
    MyChild myChild;
    MyGrandChild myGrandChild;

    myChild.myMethod();
    myGrandChild.myMethod();
}

```

![[Pasted image 20230419084627.png]]

## Multiple Inheritance 多重继承

一个子类能继承很多个父类，一样还是使用 `:` ，但之后想要继承的 class 要用 `,` 分开

```c++
// Base class  
class MyClass {  
  public:  
    void myFunction() {  
      cout << "Some content in parent class." ;  
    }  
};  
  
// Another base class  
class MyOtherClass {  
  public:  
    void myOtherFunction() {  
      cout << "Some content in another class." ;  
    }  
};  
  
// Derived class  
class MyChildClass: public MyClass, public MyOtherClass {  // 逗号分开
};  
  
int main() {  
  MyChildClass myObj;  
  myObj.myFunction();  
  myObj.myOtherFunction();  
  return 0;  
}
```

## Access Specifiers

还记得之前提到过的 `protected` 关键字吗？`public` 是可以被内部和外部 class 调用的，`private` 智能从类的内部访问，而 `protected` 不能被外部 class 调用，但是能被继承了的类调用

```c++
// Base class  
class Employee {  
  **protected: // Protected access specifier**  
    int salary;  
};  
  
// Derived class  
class Programmer: public Employee {  
  public:  
    int bonus;  
    void setSalary(int s) {  
      salary = s;  
    }  
    int getSalary() {  
      return salary;  
    }  
};  
  
int main() {  
  Programmer myObj;  
  myObj.setSalary(50000);  
  myObj.bonus = 15000;  
  cout << "Salary: " << myObj.getSalary() << "\n";  
  cout << "Bonus: " << myObj.bonus << "\n";  
  return 0;  
}
```

# Polymorphism 多态性

> 同一种操作或方法可以被不同的对象执行，且能产生不同的结果

同一个 method，被其他的类继承了之后可以被重写

```c++
#include <iostream>
using namespace std;

class Animal {
public:
    void sound() {
        cout << "This animal make a sound\n";
    }
};


class Cow : public Animal {
public:
    void sound() {
        cout << "Moo mooo\n";
    }
};


class Pig : public Animal {
public:
    void sound() {
        cout << "Wee wee\n";
    }
};


int main() {
    Animal animal;
    Cow cow;
    Pig pig;

    animal.sound();
    cow.sound();
    pig.sound();
    return 0;
}
```

![[Pasted image 20230420092746.png]]

