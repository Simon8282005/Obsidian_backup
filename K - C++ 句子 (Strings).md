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
string my
```