Conditions 其实就是这几个符号组成的，都是老朋友了

`>`, `<`, `>=`, `<=`, `==`, `!=`

### If

但需要判断 condition 时，用 If

### Else

如果 condition 为 false 时程序所要做出的反应

### Else if

让程序接下去对比第二个 condition （当第一个 condition 为 false)

```c
if (condition1) {  
	// block of code to be executed if condition1 is true
} else if (condition2) {  
   // block of code to be executed if the condition1 is false and condition2 is true 
} else {  
   // block of code to be executed if the condition1 is false and condition2 is false
}
```

### Switch

当有很多个 condition 需要做对比，当然用很多个 if 语句嵌套也行，但代码就显得很杂乱

C ++ 里判断的语句格式是这样子写的：
```c
if (condition) {  // 记住一定要有挎号，Python 则不强制要求一定要有挎号
// ...
}
```


```c
int x = 10, y = 100;

if (x < y) {
	cout << "X greater that y ";
} else {
	cout << "X smaller that y";
}
```

### 简短版 else if ？？

诶？？？else if 的简短版？就像 python 那样？非也非也

`variable = (condition) ? expressionTrue :  expressionFalse;`

啊这。。。。看都没看过啊 XDD

`?` 可以理解成原本 `if else` 语句，原本的 `if` 部分，当condition 为 true 时执行，而 `:` 就是 `else` 的部分

```c
int time = 20;  
string result = (time < 18) ? "Good day." : "Good evening.";  
cout << result;
```

XDDD

![[Pasted image 20230408170030.png]]

![[Pasted image 20230408170044.png]]

