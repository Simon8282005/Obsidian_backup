
# Break

C++ 的 break 和 python 里面是一样的，都是直接跳出循环

```c++
for (int i = 0; i <= 4; i++) {
	if (i == 3) {
		break;
	}
	cout << "I: " << i << "\n";
}
```

![[Pasted image 20230411081926.png]]

# Continue

和 python 一样，直接跳过循环

```c++
for (int i = 0; i <= 4; i++) {
	if (i == 3) {
		continue;
	}
	cout << "I: " << i << "\n";
}
```

![[Pasted image 20230411082007.png]]

在 while 循环里面也是类似的用法

```c++
int i = 0;

while (i < 5) {
	if (i == 3) {
		break;
	}
	i++;
}
```

![[Pasted image 20230411082456.png]]


```c++
int i = 0;

while (i < 5) {
	if (i == 3) {
		continue;
	}
	i++;
}
```

![[Pasted image 20230411082613.png]]

这里注意一下，如果没有放 i++ 的话会导致程序卡住，因为 continue 语句直接把下一行的 i++ 忽略并且直接从头开始

![[Pasted image 20230411082721.png]]

这样就正常了 XDD