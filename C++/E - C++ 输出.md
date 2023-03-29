`cout <<` 能理解成 Python 里的 `print`，能写上很多次，但每一次的 output 都是在结尾加上句子，并没有添加新的一行

```c
#include <iostream>

int main() {
	std::cout << "Hello World";
	std::cout << "I am learning C++";
	return 0;
}
```

