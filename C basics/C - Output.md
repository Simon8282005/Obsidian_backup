# Print text


```c
#include <stdio.h>  
  
int main() {  
  printf("Hello World!");  
  printf("I am learning C.");  
  return 0;  
}
```

Output: **HelloWorld!I Am learning C.**
# New Lines

```c
#include <stdio.h>  
  
int main() {  
  printf("Hello World!\nI am learning C.\nAnd it is awesome!");  
  return 0;  
}
```

Output: 
**Hello World!
I am learning C
And it is awesome**

![[Pasted image 20231205154232.png]]

### \\t

`printf("\tHello World")`

### \\\

`printf("Hello\\World")`

### \\"

`printf("\"Hello World\"")`

Output:
```c
        Hello World
Hello\World
"Hello World"
```

