# Introduction
Loop statements in C++ execute a block of code multiple times. They are mainly used to reduce the length of the code by avoiding redundancy. C++ supports various loops like the **for loop**, **while loop**, and **do-while loop**, each with unique syntax, advantages, and use cases. In programming, loops are control structures designed to execute a block of code multiple times, continuing until a specified condition is met.
</span>


## Types of Loops in C++
1. **for loop**
2. **while loop**
3. **do...while loop**

## C++ for Loop

### Syntax:
```cpp
for (initialization; condition; update) {
    // body of loop
}
```
```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; ++i) {
        cout << i << " ";
    }
    return 0;
}
```
