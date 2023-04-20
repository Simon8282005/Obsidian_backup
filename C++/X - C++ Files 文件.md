如果要控制文件（写入或读取）需要引用 `fstream` - stand by `file - stream`

`fstream` 包含下面三个东西:
- ofstream - Creates and writes to files
- ifstream - Reads from files
- fstream - Combination of the ofstream and ifstream

# Create and write to a file

```c++
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    // Create a file and write something into it
    ofstream my_file("filename.txt");

    my_file << "Hello there XDDD";

    my_file.close();
}
```

# Read the files

```c++
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    // Read the file
    string text;

    ifstream my_text("filename.txt");

    while (getline(my_text, text)) {
        cout << text;
    }

    my_text.close();
}
```

# 总结

- 如果是想要创建文件，使用 `ofstream`
- 如果是想要读取文件，使用了 `ifstream`
明天继续学 C++ 异常