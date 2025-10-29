# Extra Exercises: Pointer Part 1

Credits: Punyanuch Borwarnginn (email:punyanuch.bor@mahidol.ac.th)

---






## Pointer Basics: Declaration, Assignment, and Dereferencing

### Concept Recap

| Concept | Explanation | Example |
| :--- | :--- | :--- |
| **Variable** | A symbolic name associated with a value stored in memory. | `int x = 10;` |
| **Memory Address** | The location in memory (RAM) where the variable's value is stored [cite: 35, 104-105]. | `0x16b9731d8` |
| **`&` (Address-of Operator)** | An operator used to get the memory address of a variable. | `&x` (read as "address of x") |
| **Printing Addresses** | [cite_start]The `%p` format specifier is used with `printf` to display memory addresses [cite: 224-225]. | `printf("%p", &x);` |
| **Pointer** | A special variable that stores the **memory address** of another variable. | `p_num` is a pointer. |
| **Declaration** | Uses `*` to declare a pointer variable and specify the type of data it will point to. | `int *p_num;` (p\_num will store an address of an `int`) |
| **Assignment** | Storing an address (usually from `&`) into the pointer variable. | `p_num = &num;` (p\_num now points to `num`) |
| **Dereferencing** | Uses `*` to access or modify the **value** at the memory address the pointer is storing. | `*p_num = 5;` (Changes the value *at that address* to 5) |

### Which of the following statements is TRUE?
Select the **best** answer.

* [ ] A. Every variable in a C program is stored at the same memory address.
* [ ] B. The * operator is used to get the memory address of a variable.
* [ ] C. The & operator is used to get the memory address of a variable.
* [ ] D. A variable's value and its memory address are the same thing.

### What does a pointer variable store?

* [ ] A. The value of another variable
* [ ] B. The memory address of another variable
* [ ] C. The size of a variable in bytes
* [ ] D. The name of a variable



### Which operator is used to get the *address* of a variable?

* [ ] A. `*`
* [ ] B. `&`
* [ ] C. `@`
* [ ] D. `#`



###  Which operator is used to *dereference* a pointer?

* [ ] A. `*`
* [ ] B. `&`
* [ ] C. `@`
* [ ] D. `%`



### What is printed by this code?

```c
int x = 5;
int *p = &x;
printf("%d\n", *p);
```

* [ ] A. 5
* [ ] B. Memory address
* [ ] C. Garbage value
* [ ] D. Compile error


### When you pass a pointer to a function, what is actually passed?

* [ ] A. The memory address of the variable
* [ ] A copy of the variable’s value
* [ ] The variable’s name
* [ ] Nothing

### Which code correctly assigns a pointer to a variable?

```c
int a = 7;
int *p;
```

* [ ] A. `p = &a;`
* [ ] `*p = a;`
* [ ] C. `a = &p;`
* [ ] D. `&p = a;`

---



### What will be the output?

```c
int a = 3, b = 7;
int *p = &a;
*p = *p + b;
printf("%d %d", a, b);
```

* [ ] A. `10 7`
* [ ] B. `3 7`
* [ ] C. `10 10`
* [ ] D. `7 3`


## Pass by Reference


### Concept Recap

| Concept | Explanation | Example |
| :--- | :--- | :--- |
| **Pass by Value** | C's default behavior. The function receives a **copy** of the argument's value. Changes to the parameter inside the function **do not** affect the original variable in `main` [cite: 494-509, 528-530]. | `void func(int x) { x = 10; }` <br> (Calling `func(a);` does not change `a`) |
| **Pass by Reference** | (Simulated in C) The function receives a **copy** of a **memory address** (a pointer). The function can then use this address (by **dereferencing `*`**) to modify the **original** variable in `main`. | `void func(int *p) { *p = 10; }` <br> (Calling `func(&a);` changes `a` to 10) |

---


### Why did the "pass-by-value" swap function fail? 

```c
void swap(int x, int y) {
    int temp = x;
    x = y;
    y = temp;
}

int main() {
    int a = 5, b = 10;
    swap(a, b);
    printf("a=%d b=%d\n", a, b); // Output: a=5 b=10
    return 0;
}
```
* [ ] A. The function must `return` the values.
* [ ] B. The function `swap` modified its local copies of `x` and `y`, not the original variables `a` and `b`.
* [ ] C. The function must be called as `a = swap(a, b);`.
* [ ] D. The `temp` variable must be declared in `main`.




### What is the output of the following code?
```c
#include <stdio.h>

int func1(int *num1, int num2, int *num3) {
    *num1 += 1;   // a becomes 2
    num2 += 2;    // local copy 'num2' becomes 12
    *num3 += num2 + *num1 + 1; 
    printf("In func1: %d %d %d\n", *num1, num2, *num3);
    return *num1 + num2 + *num3; 
}

int main() {
    int a = 1, b = 10, c = 100;
    int *ptr = &c;
    int result = func1(&a, b, ptr);
    printf("In main: %d %d %d\n", a, b, c);
    printf("Result: %d\n", result);
    return 0;
}
```
* [ ] A. 
```
In func1: 2 12 115
In main: 2 10 115
Result: 129
```

* [ ] B. 
```
In func1: 2 12 115
In main: 2 12 115
Result: 129
```
* [ ] C. 
```
In func1: 2 12 113
In main: 2 10 113
Result: 127
```

## Pointers and Arrays

### Concept Recap

| Concept | Explanation | Example (Given: `int arr[5]; int *p;`) |
| :--- | :--- | :--- |
| **Array Name as Pointer** | When used in an expression, the name of an array (e.g., `arr`) decays into a pointer to its **first element**. | `p = arr;` <br> (Equivalent to `p = &arr[0];`) |
| **Pointer Arithmetic** | Adding/subtracting an integer `n` from a pointer moves it by `n * sizeof(data_type)` bytes to the next/previous element. | `p + 1` <br> (Points to the next element, `&arr[1]`) |
| **Access Equivalence** | Accessing array elements with subscript `[]` is equivalent to using pointer dereferencing `*()`. | `arr[i]` <br> (Is equivalent to `*(arr + i)`) |
| **Passing Arrays** | Passing an array to a function is actually passing a **pointer to its first element** (by value). | `void func(int a[])` <br> (Is equivalent to `void func(int *a)`) |

---
### Which of the following statements are TRUE?

Select **all that apply**.

* [ ] A. Given `int arr[10];`, using `arr` is equivalent to using `&arr[0]`.
* [ ] B. Given `int arr[10];`, using `arr` is equivalent to using `&arr`.
* [ ] C. If `int *p = arr;`, then `p++` and `arr++` are equivalent operations.
* [ ] D. The expression `arr[3]` is equivalent to the expression `*(arr + 3)`.
* [ ] E. The function declarations `void f(int x[10])` and `void f(int *x)` are equivalent.

### What is the output of the following code?

```c
#include <stdio.h>

int main() {
    int nums[] = {10, 20, 30, 40};
    int *p = nums; 

    printf("%d ", *p); 

    p++; 
    printf("%d ", *p); 

    p = p + 2; 
    printf("%d\n", *p); 
    return 0;
}
```
* [ ] A. 10 20 30

* [ ] B. 10 20 40

* [ ] C. 10 30 40

* [ ] D. 10 10 30




## Coding Exercises

### "Return" Multiple Values

 A function can only `return` one value. However, we can use pointers to "return" multiple values by modifying variables in `main`.

Write a function `find_min_max` that takes two integers, `x` and `y`. It should "return" the minimum and maximum of the two numbers by storing them in the pointer arguments `p_min` and `p_max`.

**Starter Code:**

```c
#include <stdio.h>

/* --- Function Prototype --- */
// TODO: Write the prototype for find_min_max
// It should accept two 'int' values and two 'int*' pointers
// It should return 'void'
void find_min_max(int x, int y, int *p_min, int *p_max);


/* --- Main Function --- */
int main() {
    int a = 17, b = 4;
    int min_val, max_val;

    // TODO: Call find_min_max here
    // Pass 'a', 'b', and the addresses of 'min_val' and 'max_val'
    find_min_max(a, b, &min_val, &max_val);

    printf("Inputs: %d, %d\n", a, b);
    printf("Min: %d\n", min_val);
    printf("Max: %d\n", max_val);
    return 0;
}


/* --- Function Definition --- */
// TODO: Write the function definition for find_min_max
void find_min_max(int x, int y, int *p_min, int *p_max) {
    if (x > y) {
        // TODO: Use dereferencing (*) to set the values
        // *p_max = ...
        // *p_min = ...
    } else {
        // TODO: Use dereferencing (*) to set the values
        // *p_max = ...
        // *p_min = ...
    }
}
```

Expected Output:
```
Inputs: 17, 4
Min: 4
Max: 17
```

---

### Update by Reference in Multiple Functions 

Write a program that reads an integer as the initial value, then performs two operations:

1. Increase the value by a given amount.  
2. Decrease the value by another given amount.  

Use two functions — `increase()` and `decrease()` — both receiving the **address** of the variable.


### Function Prototypes
```c
void increase(int *x, int amount);
void decrease(int *x, int amount);
```

### Input
The input consists of:

1. An integer — the initial value

2. Two integers — the increase amount and the decrease amount

### Example 

Input
```
100
20 15
```
Output

Display the initial value, then the updated values after each operation.
```
Initial value: 100
After increase: 120
After decrease: 105
```
---

### Manage Scores by Reference

You are asked to write a C program to manage the scores of a small class.

1. The program first reads `N` — the number of students.  
2. Then it reads `N` scores.  
3. It must:
   - Add bonus points to all scores using **pass by reference**.  
   - Find and return the **average** and **highest score** via pointer parameters.  
   - Update all scores directly through the pointer so that the changes persist in `main()`.

Use separate functions for each task:
- `void addBonus(int *arr, int n, int bonus);`  
- `void computeStats(int *arr, int n, float *avg, int *max);`

### Explanation

| Step | Function | Action |
|------|-----------|--------|
| 1 | `addBonus()` | Receives the array address and updates every score in memory directly. |
| 2 | `computeStats()` | Returns both average and maximum through pointer parameters. |
| 3 | `main()` | Prints updated array and calculated results, showing persistence of changes. |



### Function Prototypes
```c
void addBonus(int *arr, int n, int bonus);
void computeStats(int *arr, int n, float *avg, int *max);
```
### Input
The input consists of:

1. An integer `N` (number of students)
2. `N` integers representing student scores
3. An integer `bonus` for the additional points to be added

### Example 

Input
```
5
60 75 80 90 50
5
```
Output

Display the initial value, then the updated values after each operation.
```
Scores after adding bonus: 65 80 85 95 55
Average score: 76.00
Highest score: 95
```

### Starter Code

```c
#include <stdio.h>

// TODO: Write your function prototypes here


int main() {
    int n, bonus;

    // Step 1: Read number of students
    scanf("%d", &n);

    int scores[n];

    // Step 2: Read all scores
    for (int i = 0; i < n; i++) {
        scanf("%d", &scores[i]);
    }

    // Step 3: Read bonus amount
    scanf("%d", &bonus);

    // Step 4: Call function to add bonus points
    // 

    // Step 5: Call function to compute average and max
    // 

    // Step 6: Print updated scores, average, and maximum
    // (format your output like the example)

    return 0;
}

// TODO: Implement addBonus() function
// void addBonus(int *arr, int n, int bonus) {
//     // use pointer arithmetic to modify all scores
// }

// TODO: Implement computeStats() function
// void computeStats(int *arr, int n, float *avg, int *max) {
//     // calculate average and maximum using pointers
// }
```
---
### Testcase 1

Input
```
4
70 70 70 70
10
```

Output
```
Scores after adding bonus: 80 80 80 80
Average score: 80.00
Highest score: 80
```

### Testcase 2

Input
```
6
30 45 90 100 60 75
15
```


Output
```
Scores after adding bonus: 45 60 105 115 75 90
Average score: 81.67
Highest score: 115
```

### Testcase 3

Input
```
5
10 20 30 40 50
0
```


Output
```
Scores after adding bonus: 10 20 30 40 50
Average score: 30.00
Highest score: 50

```
