# int

# float

# char

For char，如果在写代码时忘记使用 `[]` 符号来设置 char 列表的大小，很有可能会遇到 `warning: excess elements in scalar initializer`  的错误

```c
char hello[10] = {'h', 'e'};

printf("%s", hello);
```
Output = **he**

如过这样写程序又要出错了

```c
char hello[2] = {'h', 'e', 'l', 'l', 'o'};
```