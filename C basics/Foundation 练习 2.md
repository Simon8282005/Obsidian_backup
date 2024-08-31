
1. Write a program to ask user to input 3 numbers.

```c
#include <stdio.h>

int main() {
    // Declare three variable to store number that use input
    printf("Please choose three number you like\n");

    int x;
    int y;
    int z;
    
    printf("First number: ");
    scanf("%d", &x);
    printf("Second number: ");
    scanf("%d", &y);
    printf("Third number: ");
    scanf("%d", &z);

    printf("Three number3 you choose is: %d, %d and %d", x, y, z);
    
    return 0;
}
```

2. Explain the command(s) you used to write the program in question 1.


3. Write a program to ask user to enter 3 characters.

```c
#include <stdio.h
  
int main() {
    // Declare three variable to store number that use input
    printf("Please choose three number you like\n");

    char x;
    char y;
    char z;

    printf("First number: ");
    scanf("%s", &x);
    printf("Second number: ");
    scanf(" %c", &y);
    printf("Third number: ");
    scanf(" %c", &z);
    
    printf("Three number you choose is: %c, %c and %c", x, y, z);
    return 0;
}
```

4. Explain the command(s) you used to write the program in question 3.


5. Write a program to let user to input 3 words.

```c
#include <stdio.h>

int main() {
    printf("Enter three words that inside your brain right now (Don't more that 12 alphabet): \n");

    int MAX = 13;
    char x[MAX];
    char y[MAX];
    char z[MAX];

    printf("First words: ");
    fgets(x, MAX, stdin);

    printf("Second words: ");
    fgets(y, MAX, stdin);

    printf("Third words: ");
    fgets(z, MAX, stdin);

    printf("Three word thay you enter is: %s, %s and %s", x, y, z);

    return 0;
}
```

6. Explain the command(s) you used to write the program in question 5.


7. Explain the difference between the programs in question 4 and 6.


8. Design a simple menu with the following output, and allow user to enter selection.


Welcome to Food
1. Rice
2. Noodle
3. Drinks
Enter your selection:


9. After the user enter the selection, display sub-menu for each selection.


```c
#include <stdio.h>

int main() {

    printf("Welcome to Food\n1. Rice\n2. Noodle\n3. Drinks\nEnter your selection: ");
    int selection;
    scanf("%d", &selection);

    if (selection == 1) {
        printf("\n1. Rice");
    } else if (selection == 2) {
        printf("\n2. Noodle");
    } else if (selection == 3) {
        printf("\n3. Drinks");
    } else {
        printf("\nSorry, we don't got this dishes inside our menu");
    }
    return 0;
}
```

10. Explain how you plan to write your program in question 9.