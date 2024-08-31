其实 For loop 主要就是要记住是怎么使用的：

### For 框架

```c
for (int i = 0; i <= 10; i ++) {
	// Your code here
	printf("Hello World");
}
```

这个 Output 是会打印出十个 hello world

这里有些魔鬼细节要注意：

**for** 循环会运行直到里面的 **statement** 为 **false**

在最后一次循环的时候，当 `i = 10`，就会进入循环里面，但是当 `i += 1，i =11`，**statement** 不符合，跳出循环

### How for loop work ?

![[Pasted image 20231225232858.png]]

在创建一个 for 循环之前，需要先 initialize，也就是初始化

```c
// 分别创建一个变量；条件；更新变量的数值，要不然这个循环就会卡死了
for (int i = 0; i <= 5; i++) {

}
```

当条件为 true，就会执行 for loop 里面的代码

当条件为 false，for loop 自动结束并跳出循环

