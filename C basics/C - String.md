### String 的 method

- **strcpy(a, b)** = copy string a into b
	-  格式为 strcpy( destination[想要 copy 进入的位置]， source[从哪里 copy 过来])

![[Pasted image 20240106142242.png]]

- **strcat (a, b)** = b 在 a 句子的尾端链接起来
	![[Pasted image 20240106142654.png]]

- **strlen(a)** = length of the string
- **strcmp(a, b)** = compare a and b string （句子的长度）
	 - return 1 if a and b string are the same
	 - return -ve if a < b
	 - return +ve if a > b

- **strchr(a, b)** = 