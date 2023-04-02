好了，已经确定了， C++ 是支持 `float` 类型的

![[Pasted image 20230402084922.png]]

重点看一下 `float` 和 `double` 数据类型，两个都是储存小数点，但 `float` 只能储存小数点后面 6-7 个号码，而 `double` 则能储存 小数点后面15 个号码，这就是为什么 `double` 会占用更多的内存的原因

### Numerics 

就和 python 是一样的，`int` 拿来储存整数，`bool` 储存 true of false, `char` 拿来储存一个字母，`string` 储存字母，`float` 和 `double` 小数点

但是，`float` and `double` 还能这样写：

```c
#include <iostream>
using namespace std;

int main() {
    float f1 = 35e3;
    double d1 = 12E4;
    cout << f1 <<"\n";
    cout << d1;
    return 0;
}
```

![[Pasted image 20230402090550.png]]

`e` & `E` 表示 10，`e3` 表示10 ^ 3，死去的 phy 又回来了。。。 XDD

### Boolean types

`true` = 1，`false` = 0 XDDD

### Characters

`char = 'B'` 
当然，也能用 ASCII 数值来表达字母

```c
#include <iostream>
using namespace std;

int main() {
    char a = 65, b = 66, c = 67;
    cout << a << "\n";
    cout << b << "\n";
    cout << c;
    return 0;
}
```

![[Pasted image 20230402091508.png]]

没想到吧 XDD

[ASCII 数值对应字母查询表](https://www.w3schools.com/charsets/ref_html_ascii.asp)

### Strings types

`string a = "Hello World"`

还能在开头添加多一个库，`#include <string>`，具体的用处之后的章节才会学到

```c
#include <string>
#include <iostream>
using namespace std;

int main() {
    string greeting = "Hello";
    cout << greeting;
return 0;
}
```

![[Pasted image 20230402092056.png]]

