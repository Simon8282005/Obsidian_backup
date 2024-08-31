
```c
#include <stdio.h>

int main() {
    char name[20];

    printf("Enter your name: ");
    gets(name);
    puts(name);
    printf("%s", name);

    // gets = scanf
    // gets();
    // puts = printf
    // puts();
    
    return 0;
}
```

- `scanf()` 只要读取到空格就会停了 (比如 Chia Chia，只会读取 Chia 而已)
- `gets()` 就能够读取一整行
- `fgets()` 作用和 `gets()` 差不多，但更加安全

### gets() vs fgets()

```c
#include <stdio.h>

int main() {
    int MAX = 15;

    // index start from zero so that only read til 14 elements      
    char buf[MAX];
    fgets(buf, MAX, stdin);
    printf("string is: %s\n", buf);

    return 0;
}
```

Output:
**Hello World and welcome to my world
string is: Hello World an**

- fgets(): 只会读取 MAX - 1 的字母并且回传给 buf，这样就不会 buffer overflow error (缓冲区溢出)
- gets(): 可不管，直接读完整行然后 pass 给 buf，compiler 报不报错关我啥事