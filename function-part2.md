# Extra Exercises: Functions Part 2

Credits: Akara Supratak (email: akara.sup@mahidol.ac.th, github: [@akaraspt](https://github.com/akaraspt))

## Variable Scope

### Concept Recap

| Concept                  | Explanation                                                                                                          |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| **Scope**                | The region of the program where a variable is valid and accessible.                                                  |
| **Local Variable**       | Declared **inside** a function or block `{ ... }`; can only be used inside that block.                               |
| **Global Variable**      | Declared **outside** of all functions; can be accessed by any function in the file.                                  |
| **Function Parameter**   | Behaves like a local variable inside that function. Changing it does **not** affect the caller’s variable.           |
| **Block Scope**          | Variables declared inside an `if`, `for`, or `while` block are limited to that block.                                |
| **Override / Shadowing** | If a variable with the same name exists in both global and local scope, the **local variable hides** the global one. |

### Which of the following statements about scope is TRUE?

Select **all that apply**.

* [ ] A. A variable declared inside a function cannot be used outside it.
* [ ] B. A global variable is automatically destroyed when a function ends.
* [ ] C. Function parameters behave like local variables of that function.
* [ ] D. Variables in different scopes cannot have the same name.
* [ ] E. Variables declared inside an `if` block can be used anywhere in the program.

### What happens to a local variable when the function finishes execution?

Select the **best** answer.

* [ ] A. It becomes a global variable.
* [ ] B. It keeps its value for the next call.
* [ ] C. It is destroyed (its memory is released).
* [ ] D. It is automatically copied into all other functions.
* [ ] E. It becomes a static variable.

### Variable Override concept

What is the output of the following code?

```c
#include <stdio.h>

int main() {
    int x = 5;
    if (1) {
        int x = 10;
        printf("%d ", x);
    }
    printf("%d\n", x);
    return 0;
}
```

* [ ] A. `10 10`
* [ ] B. `10 5`
* [ ] C. `5 10`
* [ ] D. `5 5`

**Hint:**
The `x` inside the `if` block is a **new local variable** that temporarily overrides the outer `x`.
When the block ends, the outer `x` becomes visible again.

### Fill in the Blanks: Understanding Local Scope

```c
#include <stdio.h>

void print_values() {
    int a = 3;
    printf("a=%d\n", a);
}

int main() {
    int a = 10;
    print_values();
    printf("a=%d\n", _____);   // fill in the blank
    return 0;
}
```

**Expected Output:**

```text
a=3
a=10
```

**Hint:**

- Each `a` exists in its own scope.
- The `a` inside `print_values` is local to that function.

### Fill in the Blanks: Matching by Position

```c
#include <stdio.h>

float divide(float x, float y) {
    return y / x;
}

int main() {
    float a = 3, b = 4;
    float result = divide(_____, _____);  // fill in the blanks
    printf("%d\n", result);
    return 0;
}
```

**Expected Output:**

```text
0.75
```

**Hints:**

- Arguments are matched **by position**, so the first argument corresponds to `x`, and the second corresponds to `y`.

### Lifetime of Local Variable in Function

What is the output of the following code?

```c
#include <stdio.h>

void counter(void) {
    int count = 0;
    count++;
    printf("%d\n", count);
}

int main() {
    counter();
    counter();
    counter();
    return 0;
}
```

* [ ] A. 1 2 3
* [ ] B. 1 1 1
* [ ] C. 0 1 2
* [ ] D. Compile error

**HInt:**

- Each time `counter()` is called, a new local `count` is created and destroyed after the function finishes. It does not remember previous values.

### Identify the Scope Error

Why does the following code produce an error?

```c
#include <stdio.h>

int main() {
    if (1) {
        int x = 5;
    }
    printf("%d\n", x); // ERROR: Why?
    return 0;
}
```

### Variable Name Confusion

What is the output of the following code?

```c
#include <stdio.h>

int subtract(int b, int a) {
    return b - a;
}

int main() {
    int a = 2, b = 5;
    int result = subtract(a, b);
    printf("%d\n", result);
    return 0;
}
```

* [ ] A. 3
* [ ] B. -3
* [ ] C. 7
* [ ] D. -7
* [ ] E. Compile error

**Hints:**

- What matters is **the order of arguments**, not the variable names.

### Passing by Value and Order

What is the output of the following code?

```c
#include <stdio.h>

void test(int a, int b) {
    a = a + 10;
    b = b + 20;
    printf("Inside test: a=%d, b=%d\n", a, b);
}

int main() {
    int a = 1, b = 2;
    test(b, a);
    printf("In main: a=%d, b=%d\n", a, b);
    return 0;
}
```

* [ ] A. Inside test: a=11, b=22; In main: a=1, b=2
* [ ] B. Inside test: a=21, b=12; In main: a=1, b=2
* [ ] C. Inside test: a=12, b=21; In main: a=1, b=2
* [ ] D. Compile error

**Hints:**

- The values are passed **by value** and **in order**, not by name.
- In the call `test(b, a)`, `b=2` goes into parameter `a`, and `a=1` goes into parameter `b`.

## Global vs Local Variables

### **Concept Recap**

| Concept             | Explanation                                                                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Global Variable** | Declared **outside** all functions (usually at the top of the file). Accessible by all functions in that file.                                              |
| **Local Variable**  | Declared **inside** a function or block `{ ... }`. Only accessible within that function or block.                                                           |
| **Initialization**  | Global variables are automatically initialized to `0` (or `NULL`), while local variables have **undefined (garbage)** values if not explicitly initialized. |
| **Lifetime**        | A global variable exists for the **entire program**, while a local variable exists **only during the function’s execution**.                                |
| **Best Practice**   | Avoid unnecessary global variables. Use function parameters and return values instead.                                                                      |

### Which of the following statements are TRUE about global and local variables?

Select **all that apply.**

* [ ] A. Global variables can be accessed by any function in the same file.
* [ ] B. Local variables can be accessed from any function.
* [ ] C. Global variables are initialized to zero by default.
* [ ] D. Local variables must be explicitly initialized before use.
* [ ] E. A global variable has a shorter lifetime than a local variable.

### Global vs Local Variable Override

What is the output of the following code?

```c
#include <stdio.h>

int x = 10;   // global variable

int main() {
    int x = 5;    // local variable
    printf("%d\n", x);
    return 0;
}
```

* [ ] A. 5
* [ ] B. 10
* [ ] C. Compile error
* [ ] D. Undefined

**Hint:**

- The local variable `x` **overrides (shadows)** the global `x` within the `main` function.

### Global vs Function Local Variable

What is the output of the following code?

```c
#include <stdio.h>

int value = 100;

void update() {
    int value = 50;
    printf("Inside update: %d\n", value);
}

int main() {
    printf("Before update: %d\n", value);
    update();
    printf("After update: %d\n", value);
    return 0;
}
```

* [ ] A.

  ```text
  Before update: 100
  Inside update: 100
  After update: 50
  ```

* [ ] B.

  ```text
  Before update: 100
  Inside update: 50
  After update: 100
  ```

* [ ] C.

  ```text
  Before update: 50
  Inside update: 50
  After update: 50
  ```

* [ ] D. Compile error

**Hints:**

- The `value` inside `update()` is a **new local variable** that hides the global `value` (i.e., overrides it).
- Changing it does **not** affect the global variable.

### Accessing a Global Variable inside a Function

What is the output of the following code?

```c
#include <stdio.h>

int counter = 0;

void increment() {
    counter++;
    printf("Counter in increment: %d\n", counter);
}

int main() {
    increment();
    increment();
    printf("Counter in main: %d\n", counter);
    return 0;
}
```

* [ ] A.

  ```text
  Counter in increment: 1
  Counter in increment: 1
  Counter in main: 0
  ```

* [ ] B.

  ```text
  Counter in increment: 1
  Counter in increment: 2
  Counter in main: 2
  ```

* [ ] C. Compile error

**Hint:**

- `counter` is a **global variable**, so changes inside `increment()` affect the same variable accessible by `main()`.

### Understanding Variable Lifetime

```c
#include <stdio.h>

int global = 5;

void test() {
    int local = 5;
    local++;
    global++;
    printf("local=%d global=%d\n", local, global);
}

int main() {
    test();
    test();
    return 0;
}
```

**Output:**

```text
local=6 global=6
local=6 global=7
```

**Question:** Why is `local` always `6` while `global` keeps increasing?

**Hint:**

- `local` is **recreated** each time the function is called,
- while `global` **persists** for the entire program and keeps its previous value.

### Global vs Local Conflict Update

What is the output of the following code?

```c
#include <stdio.h>

int num = 50;

void change() {
    int num = 10;
    num += 5;
    printf("Inside change: %d\n", num);
}

int main() {
    change();
    printf("In main: %d\n", num);
    return 0;
}
```

* [ ] A. Inside change: 55; In main: 55
* [ ] B. Inside change: 10; In main: 10
* [ ] C. Inside change: 15; In main: 50
* [ ] D. Compile error

**Hint:**

- The `num` in `change()` is a new local variable that hides the global `num`.

### Find and fix bugs: Accessing Global Variable

This program is trying to update a global variable `total` inside a function, but it does not work as intended. What is the problem, and how can you fix it?

```c
#include <stdio.h>

int total = 10;

void add_to_total(int n) {
    int total = 0;
    total = total + n;
    printf("Local total=%d Global total=%d\n", total, _____);
}

int main() {
    add_to_total(5);
    printf("Final Global total=%d\n", total);
    return 0;
}
```

**Expected Output:**

```text
Local total=5 Global total=15
Final Global total=15
```

### When Should You Use a Global Variable?

Select the **best** answer.

* [ ] A. When you need to share data between many functions and it changes frequently.
* [ ] B. Only when truly necessary (e.g., configuration constants, counters, or flags).
* [ ] C. Whenever you want to avoid using parameters.
* [ ] D. Always, because it simplifies function calls.
* [ ] E. Never — global variables are forbidden in C.

## Variable Override

### Concept Recap

| Concept         | Explanation                                                                                                                                                             |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Override**    | When a **local variable** uses the **same name** as a global variable (or an outer variable), the **local one temporarily overrides** the other within that scope.      |
| **Effect**      | The outer or global variable is not deleted — it is just **hidden** while the local one is active.                                                                      |
| **Access Rule** | Inside nested scopes, C always uses the **most recent (innermost)** definition of the variable name. The overridden variable becomes visible again when the block ends. |

---

### Identify Which Variable Is Used

What is the output of the following code?

```c
#include <stdio.h>

int num = 10;

int main() {
    int num = 5;
    printf("%d\n", num);
    return 0;
}
```

* [ ] A. 5
* [ ] B. 10
* [ ] C. Compile error
* [ ] D. Undefined

**Hint:**

- The local variable `num` **overrides** the global `num` inside `main()`.

### Override Across Nested Blocks

What is the output of the following code?

```c
#include <stdio.h>

int main() {
    int x = 1;
    {
        int x = 2;
        {
            int x = 3;
            printf("%d ", x);
        }
        printf("%d ", x);
    }
    printf("%d\n", x);
    return 0;
}
```

* [ ] A. `3 2 1`
* [ ] B. `1 2 3`
* [ ] C. `3 3 3`
* [ ] D. Compile error

**Hint:**

- Each `{ ... }` block defines a new `x` that **overrides** the one outside it.
- When the block ends, the outer variable becomes active again.

### Override Between Global and Local Variables

What is the output of the following code?

```c
#include <stdio.h>

int count = 100;

void print_count() {
    int count = 5;
    printf("Inside function: %d\n", count);
}

int main() {
    print_count();
    printf("In main: %d\n", count);
    return 0;
}
```

* [ ] A. Inside function: 100; In main: 100
* [ ] B. Inside function: 5; In main: 100
* [ ] C. Inside function: 5; In main: 5
* [ ] D. Compile error

**Hint:**

- The local `count` in `print_count()` **overrides** the global `count`.

### Function Parameters Also Cause Override

What is the output of the following code?

```c
#include <stdio.h>

int a = 50;

void show(int a) {
    printf("a=%d\n", a);
}

int main() {
    show(10);
    printf("a=%d\n", a);
    return 0;
}
```

* [ ] A.

  ```text
  a=50
  a=50
  ```

* [ ] B.

  ```text
  a=10
  a=50
  ```

* [ ] C.

  ```text
  a=10
  a=10
  ```

### Debug the Code (Override Confusion)

Based on the following code, why the final score is still `0` instead of `15`? How to fix it?

```c
#include <stdio.h>

int score = 0;

void add_score() {
    int score = 10;
    score += 5;
}

int main() {
    add_score();
    printf("Final score = %d\n", score);
    return 0;
}
```

**Output:**

```text
Final score = 0
```

### Fill in the Blanks: Fix the Overridden Variable

Fix the code by filling in the blanks to correctly update the global `total` variable inside the `increase` function.

```c
#include <stdio.h>

int total = 5;

void increase(void) {
    _____ = _____ + 10;   // fill in the blanks
}

int main() {
    increase();
    printf("total=%d\n", total);
    return 0;
}
```

**Expected Output:**

```text
total=15
```

---

### Nested Override Example

What is the output of the following code?

```c
#include <stdio.h>

int x = 1;

void test(void) {
    x = 2;
    {
        int x = 3;
        x++;
        printf("Inner x=%d\n", x);
    }
    printf("Outer x=%d\n", x);
}

int main() {
    test();
    printf("Global x=%d\n", x);
    return 0;
}
```

* [ ] A.

  ```
  Inner x=4
  Outer x=2
  Global x=2
  ```
* [ ] B.

  ```
  Inner x=3
  Outer x=3
  Global x=3
  ```
* [ ] C.

  ```
  Inner x=4
  Outer x=4
  Global x=4
  ```
* [ ] D. Compile error

### Why Is Override Risky?

Select the **best** answer.

* [ ] A. It causes confusion because changing a local variable doesn’t affect the global one.
* [ ] B. It saves memory and reduces bugs.
* [ ] C. It synchronizes variables automatically.
* [ ] D. It prevents compilation errors.

## Refactoring & Debugging

### Debug the Scope Error — Uninitialized Variable

```c
#include <stdio.h>

int main() {
    int a;
    if (1) {
        int b = 5;
        a = b + 2;
    }
    printf("%d %d\n", a, b);
    return 0;
}
```

**Question:** Why does this code fail to compile?

**Task:** Fix the program so that it prints both numbers correctly.

### Debug the Override Confusion

```c
#include <stdio.h>

int total = 100;

void add_total(int total) {
    total = total + 50;
}

int main() {
    add_total(total);
    printf("total=%d\n", total);
    return 0;
}
```

**Expected Output:**

```text
total=150
```

**Actual Output:**

```text
total=100
```

**Question:** Why is the result incorrect?

### Refactor — Remove Unnecessary Global Variable

```c
#include <stdio.h>

int result;

void compute_sum(int a, int b) {
    result = a + b;
}

int main() {
    compute_sum(3, 7);
    printf("sum=%d\n", result);
    return 0;
}
```

**Task:** Refactor this program so that no global variables are used.

### Refactor — Use Local Scope to Simplify Code

**Original:**

```c
#include <stdio.h>

int a = 3, b = 5;

void multiply(void) {
    printf("%d\n", a * b);
}

int main() {
    multiply();
    return 0;
}
```

**Task:**

1. Remove globals.
1. `multiply` should take parameters and print the product of its arguments.

**Expected output:**

```text
15
```

### Challenge — Fix All Scope Issues

```c
#include <stdio.h>

int n = 5;

void f() {
    int n = n + 1;
    printf("%d\n", n);
}

int main() {
    f();
    printf("%d\n", n);
    return 0;
}
```

**Question:** The code does not compile or behaves unexpectedly. Explain why, and rewrite it to correctly print:

```text
6
5
```

---

## Complicated Exercises (including quizzes from previous semesters)

Credits: Akara Supratak (akara.sup@mahidol.ac.th), Thanpon Noraset (thanapon.nor@mahidol.ac.th), Siripen Pongpaichet (siripen.pon@mahidol.ac.th), and Punyanuch Borwarnginn (punyanuch.bor@mahidol.ac.th)

### Locate a target in 2D array

Write your code in the provided section to complete a program that identifies the location of the match between the given target and the data stored in the 2-D array.

First, fill in the function `scanArrayData` to scan the data for 2-D array (i.e., `DATA`). Then, ask the user for the target number (i.e., `target`). Next, use `match` function to check whether the target matches the value in the array. Finally, print out the position of matching in a row and column number format.

In this question, the target is guaranteed to be found at least 1.

Note:

* You are NOT allowed to modify the other parts of the code, except the provided sections. Otherwise, you will get a ZERO score.
* You are NOT allowed to create new variables, except for the control variables used in the repetition statement (e.g., i or j).
* You MUST use the parameters provided in the code.
* You MUST use the functions provided in the code (`scanArrayData` and `match`)
* You are NOT allowed to use any built-in C functions.

#### main.c

```c
#include <stdio.h>

#define N 10
#define M 12
int DATA[N][M];
int target; //the given target from the user

void scanArrayData(){
  //////////  Start of your code  //////////

  /*
    TODO: Scan the 2-D array data in here
  */

  //////////  End of your code  //////////
  
}

int match(int t, int v) {

  int ismatch;

  //////////  Start of your code  //////////

  /*
    TODO: Write an algorithm to confirm the match between the target 't' and the value in DATA array 'v'
  */

  //////////  End of your code  //////////

  return ismatch;
}

int main() {

  scanArrayData();

  //////////  Start of your code  //////////

  /*
    TODO: Write a program that uses the function match to check the match of the data in the array and the target
      target must be the given global variable 'target'
        You are not allowed to compare the value directly without calling the match function
  */

  //////////  End of your code  //////////

  return 0;
}
```

#### Example Cases

##### Case 1

Sample input:

```text
0 0 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 3 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
0 3 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
3
```

Sample output:

```text
The target has been found at position[4 6]
The target has been found at position[8 1]
```

##### Case 2

Sample input:

```text
0 0 0 0 0 0 0 0 0 0 0 -5 
0 0 -5 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 -5 0 0 0 0 0 
0 -5 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 0 0 
0 3 0 0 0 0 0 0 0 0 -5 0 
0 0 0 0 0 0 0 0 0 0 0 0 
-5
```

Sample output:

```text
The target has been found at position[0 11]
The target has been found at position[1 2]
The target has been found at position[4 6]
The target has been found at position[5 1]
The target has been found at position[8 10]
```

---

### Special sum

**IMPORTANT: You can only modify the code where you see `// YOUR CODE GOES HERE` comment.**

Write a function named `find_special_sum` to find a sum of EVEN or ODD values (depending on the `option` global variable value) between the starting number and ending number (inclusively).

If the `option` value is `0`, the function will return the sum of EVEN values. For example, the starting number is 5 and the ending number is 20; the result is 6 + 8 + 10 + 12 + 14 + 16 + 18 + 20 = 104.

If the `option` value is `1`, the function will return the sum of ODD values. For example, the starting number is 5 and the ending number is 20; the result is 5 + 7 + 9 + 11 + 13 + 15 + 17 + 19 = 96.

Assume that the `option` value is always valid.

This `find_special_sum` function takes only **TWO** numbers (starting and ending numbers) as input parameters and returns a sum of even or odd values. (*Hint. make use of the global variable to check whether you need to find the sum of even or odd.*)

You have to create a function prototype and a function definition; then you have to call the function inside the `main()` function. The result from the function must be returned and printed inside the `main()`.

#### main.c

```c
#include <stdio.h>

// DO NOT MODIFY THIS GLOBAL VARIABLE
int option;

// Task 1: Function Prototype
// YOUR CODE GOES HERE

int main(void) {
  // DO NOT MODIFY THIS
  int start, end;
  scanf("%d %d %d", &start, &end, &option);

  // Task 3: Call the function and print the result here
  // YOUR CODE GOES HERE

}

// Task 2: Function Definition
// YOUR CODE GOES HERE
```

#### Example Cases

##### Case 1

Input

```text
6 10 0
```

Output

```text
24
```

##### Case 2

Input

```text
6 10 1
```

Output

```text
16
```

##### Case 3

Input

```text
3 16 1
```

Output

```text
63
```

##### Case 4

Input

```text
5 20 0
```

Output

```text
104
```

##### Case 5

Input

```text
9 200 0
```

Output:

```text
10080
```

---

### Finding the Parity of a number

#### Background

Given an integer `x`. The task is to write a program to find the parity of the
given number. The parity is computed from the sum of the binary bits in of a number.
If the sum is odd, then the parity of a number is odd, otherwise even.

For example,

- `13` has a binary representation as `1101`, so it has **odd parity**.
- `5` has a binary representation as `101`, so it as **even parity**.

To help you compute this, there are two existing functions that you can use:

- `bit_at_nth(int x, int n)` returns the bit (`0` or `1`) at a binary position such as
  - `bit_at_nth(5, 0)` returns `1`
  - `bit_at_nth(5, 1)` returns `0`.
- `num_bits(int x)` returns the number of bits of the binary representation of x such as
  - `num_bits(5)` return `3`.
  - `num_bits(13)` return `4`.

#### Instruction

Please define a function `parity_bit` that takes one integer as its argument and return `0` if the argument has even parity and `1` if the argument has odd parity. Your function must print `"[DEBUG]: parity_bit(...)\n"` at the beginning of the function.

Look for `TODO` in the `main.c`.

#### main.c

```c
#include <stdio.h>
#include <math.h>

int bit_at_nth(int x, int n);
int num_bits(int x);

// TODO: 1
// Add the function prototype here

// END TODO 1

int main() {
    printf("[DEBUG]: main(...)\n");
    int x;
    printf("Input a number: ");
    scanf("%d", &x);
    if (x <= 0) {
        printf("Invalid input.\n");
    } else {
        int partity = partity_bit(x);
        if (partity == 1) {
            printf("Odd Parity\n");
        } else if (partity == 0)   {
            printf("Even Parity\n");
        } else {
            printf("Invalid parity check\n");
        }
    }
    return 0;
}


int bit_at_nth(int x, int n) {
    printf("[DEBUG]: bit_at_nth(...)\n");
    int k;
    for (int c = 0; c <= n; c++) {
        k = x >> c;
    }
    if (k & 1) {
        return 1;
    } else {
        return 0;
    }
}

int num_bits(int x) {
    printf("[DEBUG]: num_bits(...)\n");
    return ((int) floor(log2(x))) + 1;
}

// TODO: 2
// Add the function definition here

// END TODO 2
```

#### Example Cases

##### Case 1

Inputs:

```plaintext
6
```

Expected outputs (ends with a new line):

```plaintext
[DEBUG]: main(...)
Input a number: 6
[DEBUG]: parity_bit(...)
[DEBUG]: num_bits(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
Even Parity

```

##### Case 2

Inputs:

```plaintext
755
```

Expected outputs (ends with a new line):

```plaintext
[DEBUG]: main(...)
Input a number: 755
[DEBUG]: parity_bit(...)
[DEBUG]: num_bits(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
[DEBUG]: bit_at_nth(...)
Odd Parity

```

##### Case 3

Inputs:

```plaintext
1
```

Expected outputs (ends with a new line):

```plaintext
[DEBUG]: main(...)
Input a number: 1
[DEBUG]: parity_bit(...)
[DEBUG]: num_bits(...)
[DEBUG]: bit_at_nth(...)
Odd Parity

```

---

### One name to rule them all

#### Background

Converting a currency is straightforward if you know the exchange rate. For example

- 20.0 THB is converted to 4.20 RMB using the exchange rate of 0.21.
- 42.0 RMB is converted to 197.4 THB using the exchange rate of 4.70.

In the `main.c`, we defined the exchange rates for you (`THBTORMB` and `RMBTOTHB`.)
Thus, write a program to convert the currency is a piece of cake.

*To make sure you have **fun**, we introduce a twist...*

#### Instruction

Write a program that receives an input character from the command line:

- `r` means converting from THB to RMB
- `t` means converting from RMB to THB

Then the program receives a floating-point number from the command lines, and print the converted value.

You can only get full score by **USING ONLY VARIABLES NAMED `x`,** (6 points). In other words, you can declare as many variables you need, but all of them must be named `x`. *Hint*: Variable Scopes.

**DO NOT DEFINE A NEW CONSTANT.**

#### main.c

```c
#include <stdio.h>

#define RMBTOTHB 4.70
#define THBTORMB 0.21

// ADD YOUR CODE HERE
```

#### Example Cases

##### Case 1

Inputs:

```plaintext
r
20.0
```

Expected outputs (ends with a new line):

```plaintext
Converted amount: 4.20 RMB

```

##### Case 2

Inputs:

```plaintext
0
```

Expected outputs (ends with a new line):

```plaintext
Invalid conversion type.

```

##### Case 3

Inputs:

```plaintext
t
42.2
```

Expected outputs (ends with a new line):

```plaintext
Converted amount: 198.34 THB

```
