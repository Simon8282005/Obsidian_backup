### 12/18/2023

```c
#include <stdio.h>
  

int main() {
    int id = 212;
    int password = 5394;

    // int id_input, password_input;

    printf("Enter your id: ");
    scanf("%d", &id);

    printf("Enter your password: ");
    scanf("%d, &password");

    if (id == 212 && password == 5394) {
        printf("Welcome dear programmer");
    } else {
        printf("Incorrent id or password");
    }

    return 0;
}
```

有三个小错误：
1. 
`int id = 212;
`int password = 5394;`

这两行代码储存的是用户的原本 Id 和 密码，是不能更改的

`scanf("%d", &id);` 但这一行代码就开始更改 id 的数值了

正确的做法是创建多两个变量用来储存用户输入的 id 和密码，在通过和原本的 id 和密码作比较来看是不是正确

```c
int mian() {
    int id = 212;
    int password = 5394;

	// Variable to store id and password that user enter
    int id_input, password_input;

    printf("Enter your id: ");
    // Remember assign the value to the new variable
    scanf("%d", &id_input);

    printf("Enter your password: ");
    scanf("%d, &password_input");
}
```

2. 

这个开关引号放错了
```c
scanf("%d, &password_input");
``` 

```c
scanf("%d", &password_input);
```

3. 
```c
    // 比较 id 和 id_input
    // password 和 password_input
    // 这样才能知道用户输入的 id 和 password 对不对
    if (id == 212 && password == 5394) {
        printf("Welcome dear programmer");
    } else {
        printf("Incorrent id or password");
    }
```

Full code
```c
#include <stdio.h>

int main() {
    int id = 212;
    int password = 5394;

    int id_input, password_input;

    printf("Enter your id: ");
    scanf("%d", &id_input);

    printf("Enter your password: ");
    scanf("%d", &password_input);

    if (id_input == id && password_input == password) {
        printf("Welcome dear programmer");
    } else {
        printf("Incorrent id or password");
    }
    return 0;

}
```