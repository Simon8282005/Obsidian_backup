这是昨天一开始写的代码，有些看不是很懂呢

```c
#include <iostream>
using namespace std;

int main() {
	cout << "Hello World";
	return 0;
}
```

现在到了手撕代码的时候了 XDDD

`#include <iostream>` 就是 Python 和 Java 里的 `import` 功能，让我们能够使用 Input 和 Output 来完成工作（这里的 Ouput 就是要打印出一句 `Hello World`

`using namespace std;` 表示这个文件使用标准命名空间 `std` 中的变量和函数

`int main() {}` 不用说，和 Java 里的 `public class Hello_World {}` 一样的，都是一个主函数（但为什么 C++ 里的是 int 类型啊 XDDD

`cout << "Hello World";` 那个字念 (see-out) ，就是打印的意思咯，它是由 std 提供的函数

其实如果觉得用 `using namespace std;` 很烦的话，也可以这样子写的：

```c
#include <iostream>

int main() {
	std::cout << "Hello World";
	return 0;
}
```

看吧 XDDD 没有写 std 直接报错

![[Pasted image 20230329075248.png]]![[Pasted image 20230329075255.png]]
