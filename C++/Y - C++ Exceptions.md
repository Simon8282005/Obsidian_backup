Exceptions 叫做异常

想要避免程序出错时崩溃就需要使用下面这几个关键字了：

- `try` - 尝试一下下面的代码块，看看有没有错误， if error，交给 catch
- `throw` - 主动抛出异常
- `catch` - 显示出异常信息，但不会使整个程序崩溃关闭
`try` & `catch` 是一对的：

```c++
try {  
  // Block of code to try  
  throw exception; // Throw an exception when a problem arise  
}  
catch () {  
  // Block of code to handle errors  
}
```

```c++
#include <iostream>
using namespace std;

int main() {
    try {
        int age = 15;
        if (age >= 18) {
            cout << "You are old already. ";
        } else {
            throw(age);
        }
    }
    catch (int num) {
        cout << "You are not old enough\n";
        cout << "Your age are: " << num;
    }
    return 0;
}
```

上面的例子中，我们已经知道了将会被抛出的错误类型，如果不知道，就可以使用 `...` 来代替 num

```c++
catch (...) {  
  cout << "Access denied - You must be at least 18 years old.\n";  
}
```