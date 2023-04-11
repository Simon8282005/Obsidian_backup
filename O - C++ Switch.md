```cpp
switch(expression) {  // 表达
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
```

Switch 是用来判断很多个相似的状态 (conditions) 时使用的

**default** 关键字就相当于 if 语句里的 else，当全部都不 match 时执行

**break** 也是需要记得不要忘了，要不然就像 while 循环一样卡死了。。。