### Strings

C++ 中想要使用 String 数据类型，需要先 include 一个库先

```c
#include <string>

string greeting = "Hello XDD";
```

### Strings Concatenation 句子衔接

和 Python 里一样，可以用 + 来衔接两个句子

```c
string first_name = "Simon";
string last_name = "CY";

string full_name = first_name + last_name;
std::cout << full_name;
```

但是，还能用 `append()` 来把两个句子连接在一起呢 XDDD

```c
string first_name = "Simon";
string last_name = "CY";

string full_name = first_name.append(last_name);
std::cout << full_name;
```

好家伙，Python 的 append() 只能用在列表阿喂 XDD

使用 `+` 时，确保两个变量的数据类型是要一样的，要么都是 int，有要么都是 string，要不然。。。你懂的

### String length

使用 `length()` 来获得一串句子的长度

```c
#include <iostream>
#include <string>
using namespace std;

int main() {
  string txt = "ABCDEFGHIJKLMNO PQRSTUVWXYZ";
  cout << "The length of the txt string is: " << txt.length();  // Output = 27, 因为空格也算哦 XDD
  return 0;
}
```

或者是想要用 `size()` 也可以，都一样的

### Access string

我发现 string 在 C++ 里背搞得很像 Python 的列表诶。。。还能这样写啊？

`cout << my_string[0]`

![[Pasted image 20230404090306.png]]

额不对，Python 里面也能这样写的 XDD

还能改变 string 的字母诶

```c
string my_string = "Hello";
my_string[1] = "a"
cout << my_string;  // Output = Hallo XDDD
```

### Special character

下面这个句子会出现错误，因为 C++ 以为你放的双引号就是句子的重点了，为了解决这个问题就要用到 `\"` 了，原理和 `\n` 相同

![[Pasted image 20230404090450.png]]

`string txt = "We are the so-called \"Vikings\" from the north.";`

![[Pasted image 20230404090700.png]]

![[Pasted image 20230404090707.png]]

### User Input Strings

emm... `cin` 的用法在 [[H - C++ 输入 (User Input)]] 里有提到，但是，但是，只能用来读取一句句子而已

就算你输入 "Simon CY", output 的结果也是 "Simon" 而已

用 `getline(cin, string_variable)` 来解决这个问题

```c
string full_name
cout << "What\'s your name ?: '";
getline(cin, full_name);
cout << full_name;  // Output = Simon CY
```

### Omitting Namespace （省略 Namespace）

可以不用一直写 `using namespcae std;` 的，但是相对的，之后我们每一个使用到 std 库里面的函数名称都需要在前面加一个 `std::`

```c
#include <iostream>
#include <string>

// x using namespace std;
int main {
	std::cout << "Hello World";
	std::string greeting = "你好世界";
	return 0;
}
```