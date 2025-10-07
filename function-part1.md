# Extra Exercises: Functions Part 1

Credits: Akara Supratak (email: akara.sup@mahidol.ac.th, github: [@akaraspt](https://github.com/akaraspt))

## What is a Function?

### **Why do we use functions in C programming?**

Select the **best** answer.

* [ ] A. To make the code run faster automatically.
* [ ] B. To break the program into smaller, reusable, and manageable parts.
* [ ] C. To avoid using variables in the main program.
* [ ] D. Because C requires every program to have multiple functions.
* [ ] E. To reduce the size of the compiled executable file.

### **When should you consider using a function in your program?**

Select the **best** answer.

* [ ] A. When you need to repeat a specific task in multiple places.
* [ ] B. When the program has more than 10 lines of code.
* [ ] C. Only when working in a team.
* [ ] D. When you want to reduce the number of variables.
* [ ] E. When the compiler gives an error.

## Define a Function

Here’s the revised **multiple-choice questions in Markdown format** with **multiple correct answers**, suitable for testing understanding of **function header vs. function body**:

### **Which of the following are valid *function headers* in C?**

Select **all that apply**.

* [ ] A. `int add(int x, int y);`
* [ ] B. `void greet();`
* [ ] C. `{ return x + y; }`
* [ ] D. `int add(int x, int y) { return x + y; }`
* [ ] E. `#include <stdio.h>`

### **Which of the following are valid *function bodies* in C?**

Select **all that apply**.

* [ ] A. `int sum(int a, int b);`
* [ ] B. `{ return a + b; }`
* [ ] C. `{ printf("Hello!\n"); }`
* [ ] D. `int greet();`
* [ ] E. `greet();`

### **Which of the following are valid return types for functions in C?**

Select **all that apply**.

* [ ] A. `int`
* [ ] B. `double`
* [ ] C. `void`
* [ ] D. `char`
* [ ] E. `char*`
* [ ] E. `struct Student` (assume that `Student` is a defined struct)
* [ ] F. `function`

### **How should you determine the return type of a function in C?**

Select the **best** answer.

* [ ] A. Always use `int` as the return type.
* [ ] B. Choose the largest numeric type to avoid overflow.
* [ ] C. Choose the return type based on the kind of value the function should return.
* [ ] D. Use `void` for every function to simplify code.
* [ ] E. Let the compiler decide automatically.

Great idea. Here’s a set of **code-based fill-in-the-blank questions** (Markdown) where students must supply either the **return type** or the **return value**. Each question includes a short prompt and a code snippet with `_____` for the blank. An answer key is at the end.

### Fill in the **return type**

Return the sum of two integers.

```c
_____ add(int a, int b) {
    return a + b;
}
```

Return the sum of an integer and a floating-point number.

```c
_____ add(int a, float b) {
    return a + b;
}
```

Print a message; this function should not return any value.

```c
_____ print_msg(void) {
    printf("Hello, students!\n");
}
```

This function returns `0` on success and `-1` on failure.

```c
_____ save_value(int x) {
    if (x >= 0) {
        // pretend to save; success
        return 0;
    } else {
        return -1;
    }
}
```

### Fill in the **return value**

Return the area of a circle given radius `r`. Use `pi = 3.141592653589793`.

```c
double circle_area(double r) {
    // return the computed area
    return _____;
}
```

Return a C string greeting. Assume the function signature is correct.

```c
const char* greet(void) {
    // return a string literal
    return _____;
}
```

Given two points, return their **midpoint** as a `Point`.
Assume `struct Point { double x, y; };` is defined.

```c
Point midpoint(Point a, Point b) {
    // return a composite literal
    return _____;
}
```

Return `1` if `x` is even, otherwise `0`. (Use the given signature.)

```c
int is_even(int x) {
    return _____;
}
```

Excellent — moving on to **function calls** is a natural next step after teaching function headers, bodies, and return types.

Here’s a structured breakdown of how we can cover this topic for your **Fundamentals of C Programming** class, followed by sample **multiple-choice** and **code-based** questions in Markdown.

## Function Calls in C

| Concept                    | Explanation                                                                                            |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Function call**          | Invoking a function by using its name followed by parentheses containing arguments, e.g. `sum(3, 5);`. |
| **Call vs. Definition**    | Defining a function explains what it does. Calling it actually executes it.                            |
| **Arguments / Parameters** | When calling, you pass *arguments*; they match the function’s *parameters*.                            |
| **Return value usage**     | You can ignore the return value, print it, or assign it to a variable.                                 |
| **Call order**             | Functions must be either defined before the call or declared via a **prototype**.                      |

**Example:**

```c
#include <stdio.h>

int add(int a, int b);   // function prototype

int main() {
    int result = add(2, 3);   // function call
    printf("%d\n", result);
    return 0;
}

int add(int a, int b) {   // function definition
    return a + b;
}
```

### **Which of the following are valid function calls in C?**

Select **all that apply**.

* [ ] A. `printHello();`
* [ ] B. `sum(5, 10);`
* [ ] C. `int add(2, 3);`
* [ ] D. `return x + y;`
* [ ] E. `void greet();`

### **What happens during a function call in C?**

Select the **best** answer.

* [ ] A. The code inside the function is copied into `main()`.
* [ ] B. The program execution jumps to the function definition, runs it, then returns to the caller.
* [ ] C. A new variable is created with the same name as the function.
* [ ] D. The function is recompiled at runtime.
* [ ] E. Nothing happens; calls are just labels.

### **Complete the function call to compute the square of 7**

```c
#include <stdio.h>

int square(int x) {
    return x * x;
}

int main() {
    int result = _____;
    printf("%d\n", result);
    return 0;
}
```

### **Call the function `greet()` inside `main()`**

```c
#include <stdio.h>

void greet(void) {
    printf("Welcome!\n");
}

int main() {
    _____;
    return 0;
}
```

### **Use the return value of a function call in an expression**

```c
#include <stdio.h>

int doubleIt(int n) {
    return n * 2;
}

int main() {
    int total = 5 + _____;
    printf("%d\n", total);
    return 0;
}
```

## Parameter Passing in C (Pass-By-Value)**

In C, **all function arguments are passed by value**.
This means:

* When you call a function, **copies** of the arguments are passed to the function’s parameters.
* Any changes made to the parameters **do not affect the original variables** in the caller.
* If you want a function to modify the caller’s variable, you must pass a **pointer**.

**Example:**

```c
#include <stdio.h>

void changeValue(int x) {
    x = 100;    // this only changes the local copy
}

int main() {
    int a = 5;
    changeValue(a);
    printf("%d\n", a);   // still prints 5
    return 0;
}
```

### **What happens when you pass a variable to a function in C?**

Select the **best** answer.

* [ ] A. The function modifies the original variable directly.
* [ ] B. A copy of the variable’s value is passed to the function.
* [ ] C. The function shares a reference automatically.
* [ ] D. The variable is moved to the function’s scope permanently.
* [ ] E. The function allocates new memory for the variable globally.

### **Which of the following statements are TRUE about parameter passing in C?**

Select **all that apply**.

* [ ] A. Arguments are passed by value.
* [ ] B. Modifying parameters inside a function does not affect the original variables.
* [ ] C. Variables are always passed by reference automatically.
* [ ] D. Passing a variable to a function changes its memory address.
* [ ] E. To modify a variable in the caller, you need to use pointers.

### **What will be the output?**

```c
#include <stdio.h>

void modify(int n) {
    n = 99;
}

int main() {
    int x = 10;
    modify(x);
    printf("%d\n", x);
    return 0;
}
```

* [ ] A. 99
* [ ] B. 10
* [ ] C. Compile error
* [ ] D. Undefined
* [ ] E. 0

### **Fill in the blanks to pass a value to a function and print the result**

```c
#include <stdio.h>

int square(int n) {
    return n * n;
}

int main() {
    int num = 4;
    int result = square(_____);  // fill in the blank
    printf("%d\n", result);
    return 0;
}
```

### **Identify the correct output**

```c
#include <stdio.h>

void set_to_zero(int y) {
    y = 0;
}

int main() {
    int z = 7;
    set_to_zero(z);
    printf("%d\n", z);
    return 0;
}
```

* [ ] A. 0
* [ ] B. 7
* [ ] C. Undefined
* [ ] D. Depends on compiler
* [ ] E. Segmentation fault

Great—let’s level up with a single, richer lab that forces students to use **function headers/bodies, return types, function calls, and pass-by-value**. Everything below is in Markdown and ready to drop into your course site.

---

## Complicated Exercises

### Sum of Squares

Use the provided `square` and `sum` functions to compute the sum of the squares of two numbers.

```c
#include <stdio.h>

/* Prototypes */
int square(int x);
int sum(int a, int b);

/* Definitions */
int square(int x) {
    return x * x;
}

int sum(int a, int b) {
    return a + b;
}

int main(void) {
    int a, b;
    scanf("%d %d", &a, &b);
    // TODO: Use square() and sum() to compute a² + b² and print it
    return 0;
}
```

**Input:**

```text
3 4
```

**Expected Output:**

```text
25
```

---

### **Function Call Composition**

Use the `min`, `max`, and `sum` functions to compute `max(a,b) + min(a,b)` without writing extra if/else.

```c
#include <stdio.h>

int min(int a, int b);
int max(int a, int b);
int sum(int a, int b);

int min(int a, int b) { return (a < b) ? a : b; }
int max(int a, int b) { return (a > b) ? a : b; }
int sum(int a, int b) { return a + b; }

int main(void) {
    int x, y;
    scanf("%d %d", &x, &y);
    // TODO: Call the functions to compute max(x,y)+min(x,y) and print the result
    return 0;
}
```

**Input:**

```text
8 3
```

**Expected Output:**

```text
11
```

---

### Pure Numeric Utilities

Implement and use small, reusable functions.

**Required functions (students implement):**

1. `int is_even(int x);` — return `1` if even, else `0`.
2. `int is_prime(int x);` — return `1` if `x` is a prime number (≥2), else `0`.
   * Prime numbers are integers greater than 1 that have no positive divisors other than 1 and themselves.
   * A simple method is to check divisibility from `2` up to `sqrt(x)` (but without using pointers).
3. `int abs_i(int x);` — integer absolute value (don’t use `abs()` from `<stdlib.h>`).
4. `int gcd(int a, int b);` — Euclid’s algorithm, `gcd(a,0)=abs(a)`.
5. `int lcm(int a, int b);` — `lcm(a,b)=0` if `a==0 || b==0`, else `abs(a / gcd(a,b) * b)` (order avoids overflow in typical inputs).
6. `int pow_i(int base, int exp);` — integer power for `exp>=0` (iterative).

**Starter (students fill the TODOs):**

```c
#include <stdio.h>

/* ---- Prototypes ---- */
// TODO: is_even, is_prime, abs_i, gcd, lcm, pow_i

int main(void) {
    int a,b,base,exp;
    if (scanf("%d %d %d %d", &a, &b, &base, &exp) != 4) return 0;

    printf("even(a)=%d even(b)=%d\n", /* TODO: is_even(a) */, /* TODO: is_even(b) */);
    printf("prime(a)=%d prime(b)=%d\n", /* TODO: is_prime(a) */, /* TODO: is_prime(b) */);
    printf("abs(a)=%d abs(b)=%d\n",   /* TODO */,                /* TODO */);
    int g = /* TODO: gcd(a,b) */;
    int L = /* TODO: lcm(a,b) */;
    int p = /* TODO: pow_i(base, exp) */;

    printf("gcd=%d lcm=%d pow=%d\n", g, L, p);
    return 0;
}

/* ---- Definitions ---- */
// TODO: is_even
// TODO: is_prime
// TODO: abs_i
// TODO: gcd
// TODO: lcm
// TODO: pow_i
```

**Input:**

```text
6 15 3 4
```

**Expected Output:**

```text
even(a)=1 even(b)=0
prime(a)=0 prime(b)=0
abs(a)=6 abs(b)=15
gcd=3 lcm=30 pow=81
```

---

### Digit Analysis Functions

Write multiple functions to analyze the digits of an integer. This exercise helps students practice writing **several related functions** and using them together in a program.

Implement the following functions:

```c
int count_digits(int n);
int sum_digits(int n);
int product_digits(int n);
int is_palindrome_number(int n);
```

* `count_digits(n)`: Returns the number of digits in `n`. For example, `count_digits(1234)` returns `4`.
* `sum_digits(n)`: Returns the sum of all digits. For example, `sum_digits(1234)` returns `10`.
* `product_digits(n)`: Returns the product of all digits. For example, `product_digits(1234)` returns `24`.
* `is_palindrome_number(n)`: Returns `1` if `n` reads the same forwards and backwards (e.g., `1221`), else `0`.

> Assume `n` is non-negative.

**Function Prototypes:**

Place the following prototypes **above `main()`**:

```c
int count_digits(int n);
int sum_digits(int n);
int product_digits(int n);
int is_palindrome_number(int n);
```

**Starter Code:**

```c
#include <stdio.h>

/* ---- Prototypes ---- */
int count_digits(int n);
int sum_digits(int n);
int product_digits(int n);
int is_palindrome_number(int n);

int main(void) {
    int n;
    scanf("%d", &n);

    printf("digits=%d\n", count_digits(n));
    printf("sum_digits=%d\n", sum_digits(n));
    printf("product_digits=%d\n", product_digits(n));
    printf("palindrome=%d\n", is_palindrome_number(n));

    return 0;
}

/* ---- Definitions ---- */
// TODO: Write the function definitions here
```

**Case 1:**

**Input:**

```text
1221
```

**Expected Output:**

```text
digits=4
sum_digits=6
product_digits=4
palindrome=1
```

**Case 2:**

**Input:**

```text
305
```

**Expected Output:**

```text
digits=3
sum_digits=8
product_digits=0
palindrome=0
```

---

### Refactoring Duplicated Code

Students are given code with **repeated logic**, and asked to refactor by **extracting a function** and **replacing duplicated code with function calls**.

#### Refactor Average Calculation

```c
#include <stdio.h>

int main(void) {
    int a, b, c, d;
    scanf("%d %d %d %d", &a, &b, &c, &d);

    // Compute average of a,b
    double avg1 = (a + b) / 2.0;
    printf("avg1=%.2f\n", avg1);

    // Compute average of c,d
    double avg2 = (c + d) / 2.0;
    printf("avg2=%.2f\n", avg2);

    return 0;
}
```

**Task:**

* Write a function

  ```c
  double average(int x, int y);
  ```

  that computes the average of two integers.
* Replace the duplicated code in `main` with calls to `average`.

**Input:**

```text
10 20 30 50
```

**Expected Output:**

```text
avg1=15.00
avg2=40.00
```

#### Refactor Repeated Absolute Value Code

```c
#include <stdio.h>

int main(void) {
    int a, b, c;
    scanf("%d %d %d", &a, &b, &c);

    if (a < 0) a = -a;
    printf("%d\n", a);

    if (b < 0) b = -b;
    printf("%d\n", b);

    if (c < 0) c = -c;
    printf("%d\n", c);

    return 0;
}
```

**Task:**

* Extract the repeated absolute value logic into

  ```c
  int abs_i(int x);
  ```

* Use this function for `a`, `b`, `c`.

**Input:**

```text
-3 7 -8
```

**Expected Output:**

```text
3
7
8
```

---

### Debugging Exercises

Given the following code to compute GCD, please find and fix the bugs.

```c
#include <stdio.h>

int gcd(int a, int b) {
    while (a != b) {
        if (a > b)
            b = b - a; 
        else
            a = a - b;
    }
    return a;
}

int main(void) {
    int x = 12, y = 18;
    printf("%d\n", gcd(x, y));
    return 0;
}
```

**Expected Output:**

```text
6
```
