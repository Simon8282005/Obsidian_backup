
```c
#include <stdio.h>

int main() {
    int n;
    int a;
    int b;
    int result;

    printf("\nEnter the number of integers to be processed: ");
    scanf("%d", &n);

	// First
    printf("\nEnter an integer: ");
    scanf("%d", &a);
    // a = 3

    // if n = 4, only loop for 3 times
	// First time: 1 (a) <> 4 (n) = true
	// Second time: 2 (a) <> 4 (n) = true
	// Third time: 3 (a) <> 4 (n) = true
	// Quard time: 4 (a) <> 4 (n) = false
    for (int i = 1; i < n; i++) {
        printf("\nEnter next integer: ");

        // resutl = 6
        scanf("%d", &b);
        // if 3 < b

        if (a < b) {
            result = a;
        } else { // a > b
            result = b;
        }
    }

    printf("\nThe smallest num is: %d", result);

    return 0;
}
```

`n` = 用来表示 loop 的数量
`a, b` = 用来保存用户的输入，并且做比较

当你需要做比较时，最少需要三个变量：
1. 第一个变量
2. 第二个变量
3. 第三个变量，表示结果

```c
if (a < b) {
	result = a;
} else {
    result = b;
}
```

**当 a < b，表示 a 是最小的，但是当 a > b (表示 b 比 a 小)，result 就是等于 b**
