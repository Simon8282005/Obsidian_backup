
1. What is data type?
	**The type of value for a variable**

2. What are the data types in C programming?
	**int (integer), float, double, long, char**

3. Declare an integer variable – a
```c
int a = 0;
```

4. Declare 3 integer variables - a,b,c
```c
int a = 1, b = 2, c = 3
```

5. What is the difference between Initialization and declaration?
	**declare is create a variable but did not assign any values for it
	initialization is create a variable and assign a value for it**

6. Initialize 3 float variables – b,c,d
```c
float b = 0.1, c = 0.2, d = 0.3
```

7. What is the basic structure format of a C program?
```c
#include <stdio.h>

int main() {
	// Main function
	return 0;
}
```

8. Explain the basic structure format of a C program.

`#include <stdio.h>` **import the header file library name stdio.h so that we can work with input and output in this program**

`int main() {` **declare a function that name main, act as the main function for this program**

`// Main function` **a comments, use to describe the uses for the main function**

`return 0;` **the end of the program, terminates the main function with return value 0**

9. Write a program to display the following:
Student ID Class
       A 1001 FIS1
       B 1002 FIS2
       C 1003 FIS3

```c
#include <stdio.h>

int main() {
    // Declare a char list
    char name[] = {'A', 'B', 'C'};
    int id[] = {1001, 1002, 1003};
    // two dimension array
    // first argument present rows
    // second argument present columns
    // at the last of array c will automatic end with \0
    // so the length of array need to plus one
    char class[3][5] = {"FIS1", "F1S2", "F1S3"};

    for (int i = 0; i <= 2; i++) {
        printf("%c ", name[i]);
        printf("%d ", id[i]);
        printf("%s\n", class[i]);
    }
    
    return 0;
}
```

10. What command(s) you used to write the program in question 9?

`char name[]`, `int id[]` and `char class[3][5]` to create a array
`for` loop to print out all the text that use less code
`printf()` with difference format specifiers to print out all the text

