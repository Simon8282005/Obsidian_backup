1. Write a program to add 2 decimal numbers

```c
#include <stdio.h>

int main() {
    float num1;
    float num2;

    printf("Type first decimal number: \n");
    scanf("%f", &num1);

    printf("Type second decimal number: \n");
    scanf("%f", &num2);

    float sum = num1 + num2;
    printf("The sum of this two number is: %0.2f", sum);

    return 0
}
```

2. Write a program to add 2 whole numbers

```c
#include <stdio.h>

int main() {
    int num1;
    int num2;

    printf("Type first integer number: \n");
    scanf("%d", &num1);

    printf("Type second integer number: \n");
    scanf("%d", &num2);

    int sum = num1 + num2;
    printf("The sum of this two number is: %i", sum);

    return 0;
}
```

3. Write a program to subtract 2 numbers

```c
#include <stdio.h>

int main() {
    int num1;
    int num2;

    printf("Type first integer number: \n");
    scanf("%d", &num1);

    printf("Type second integer number: \n");
    scanf("%d", &num2);

    int sum = num1 - num2;
    printf("The sum of this two number is: %i", sum);

    return 0;
}
```

4. Write a program to divide 2 numbers

```c
#include <stdio.h>

int main() {
    int num1;
    int num2;

    printf("Type first integer number: \n");
    scanf("%d", &num1);

    printf("Type second integer number: \n");
    scanf("%d", &num2);

    int sum = num1 / num2;
    printf("The sum of this two number is: %i", sum);

    return 0;
}
```

5. Write a program to do all the functions of question 1,2,3,4



6. Modify the program in question 5 to allow user selection of the mathematical functions of any 2 numbers.


7. Explain your answer for question 6.


8. Highlight the commands used to achieve the output for question 6.