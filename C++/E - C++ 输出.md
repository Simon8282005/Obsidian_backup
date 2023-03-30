`cout <<` 能理解成 Python 里的 `print`，能写上很多次，但每一次的 output 都是在结尾加上句子，并没有添加新的一行

```c
#include <iostream>

int main() {
	std::cout << "Hello World";
	std::cout << "I am learning C++";
	return 0;
}
```

![[Pasted image 20230330074307.png]]

如何要添加新的一行呢，没记错的话 python 里面是用 `\n` XDDD

没想到 C++ 也同理

```c
#include <iostream>

int main() {
	std::cout << "Hello World \n";
	std::cout << "I am learning C++";
	return 0;
}
```

![[Pasted image 20230330074328.png]]

如果是两个 `\n` 会在两个句子中间创建一个空行

```c
#include <iostream>

int main() {
	std::cout << "Hello World";
	std::cout << "I am learning C++";
	return 0;
}
```

Output:

![[Pasted image 20230330073719.png]]

### 另外一种方法

如果觉得 `\n` 很麻烦的话，可以用另外一种方法

```c
#include <iostream>

int main() {
	std::cout << "Hello World" << end1;
	std::cout << "I am learning C++";
	return 0;
}
```

![[Pasted image 20230330074437.png]]

Ohhh....原来 `\` 就是 insert 的意思呀 XDDD `\n` 就是 new line 的意思咯

![[Pasted image 20230330073900.png]]

### `\t`

```c
#include <iostream>
using namespace std;

int main() {
    cout << "Hello World\t";
    cout << "I am learning C++";
    return 0;
}

```

![[Pasted image 20230330074508.png]]

### `\\`

![[Pasted image 20230330074603.png]]

### `\"`

![[Pasted image 20230330074657.png]]

意思 XDDD