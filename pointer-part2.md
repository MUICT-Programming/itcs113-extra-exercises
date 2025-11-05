# Extra Exercises: Pointer Part 2

Credits: Punyanuch Borwarnginn (email:punyanuch.bor@mahidol.ac.th)

---
## Pointers and Arrays

### 1.1 Relationship between Arrays and Pointers
- In C, the **name of an array** (e.g., `arr`) is a **constant pointer** to its first element.  
  Example:  
  ```c
  int arr[5] = {1,2,3,4,5};
  int *p = arr;        // p points to arr[0]
  printf("%d", *(p+2)); // prints 3
  ```
- `arr[i]` is **equivalent to** `*(arr + i)`  
  and `p[i]` is **equivalent to** `*(p + i)`  

### 1.2 Passing Arrays to Functions
- When an array is passed to a function, it **decays into a pointer**:  
  ```c
  void printArr(int *a, int n);
  ```
  So changes inside the function will affect the original array.

| Concept | Explanation | Example |
| :--- | :--- | :--- |
| **Pointer Arithmetic** | Adding `n` to a pointer moves it `n * sizeof(type)` bytes, effectively pointing to the n-th element from the current one. | `*(arr + 3)` access `arr[3]` |
| **Subscript Equivalence** | `arr[i]` is defined by the C language to be identical to `*(arr + i)` . | `nums[2]` is same as `*(nums + 2)` |
| **Pointer Subscript** | A pointer variable can also use subscript notation. [cite_start]`p[i]` is identical to `*(p + i)` . | `int *p = arr;` <br> `p[2]` is same as `*(p + 2)` |
| **Function Arguments** | `void func(int a[])` and `void func(int *a)` are equivalent declarations. The compiler always treats `int a[]` as `int *a` in a function parameter list . | `void f(int arr[])` is same as `void f(int *arr)` |

---
## Checkpoint Questions

### What does the name of an array represent in C?
* [ ] A. Memory size
* [ ] B. Address of first element
* [ ] C. Total number of elements
* [ ] D. None of the above

### Given the following code:
```c
int a[3] = {10, 20, 30};
int *p = a;
```
What does `*(p + 2)` evaluate to?

* [ ] A. 10
* [ ] B. 20
* [ ] C. 30
* [ ] D. Compiler error


### When an array is passed to a function, which of the following is true?
* [ ] A. The entire array is copied to the function
* [ ] B. Only the address of the first element is passed
* [ ] C. The address of the last element is passed
* [ ] D. None of the above

### Which expression correctly accesses the 5th element using a pointer p?
* [ ] A. `*p + 5`
* [ ] B. `*(p + 5)`
* [ ] C. `p[5]*`
* [ ] D. `(*p)[5]`

### What is wrong with the following line of code?
`scanf("%d", arr);`

* [ ] A. Should use `&arr`
* [ ] B. Should use `arr + 0`
* [ ] C. Nothing — it’s correct as written
* [ ] D. Must use a loop to read all elements

### Which two function declarations are equivalent to the compiler? 

* [ ] A. `void func(int arr[10])` and `void func(int arr[5])`
* [ ] B. `void func(int arr[])` and `void func(int *arr)`
* [ ] C. `void func(int *arr)` and `void func(int **arr)`
* [ ] D. `void func(int arr)` and `void func(int *arr)`

### Output of Passing an Array

What is the output of the following code?
```c
#include <stdio.h>

void func1(int *arr, int n) {
    int i;
    for (i=0 ; i<n ; i++) {
        arr[i] = arr[i] * 2; // Double each element
    }
}

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    func1(arr, 5);
    
    int i;
    for (i=0 ; i<5 ; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    return 0;
}
```
* [ ] A. 1 2 3 4 5

* [ ] B. 2 4 6 8 10

* [ ] C. 1 4 9 16 25

* [ ] D. Compile Error


## Coding Exercises


### Normalize Scores

Write a function
```c
void normalize(float *scores, int n);
```
that divides each element by the **maximum score** so that the highest value becomes **1.00**.  
All values should be updated **in-place**, meaning the original array is changed directly — no new array is created.



### Rules

- Use **pointers** (`float *p`) to access each element; avoid using square brackets `[]` inside the function.  
- You may use temporary variables to store the max value.  
- After normalization, print the modified array, displaying each value rounded to **two decimal places**, separated by a space.  
- The function doesn’t return anything; it just modifies the array.  


### Starter Code

```c
#include <stdio.h>

void normalize(float *scores, int n);

int main() {
    int n;
    scanf("%d", &n);
    float s[n];
    for (int i = 0; i < n; i++) scanf("%f", &s[i]);
    normalize(s, n);
    return 0;
}

void normalize(float *scores, int n) {
    // TODO: Step 1 – find the maximum score using pointer arithmetic
    // TODO: Step 2 – divide each element by max (modify array in-place)
    // TODO: Step 3 – print normalized values with two decimal places
}
```



### Example Input

```
5
30 60 90 45 15
```

### Expected Output

```
0.33 0.67 1.00 0.50 0.17
```


### Explanation of Output

| Step | Action | Result |
|------|---------|---------|
| 1 | Find max value | 90 |
| 2 | Divide each by 90 | [0.33, 0.67, 1.00, 0.50, 0.17] |
| 3 | Print formatted to 2 decimals | 0.33 0.67 1.00 0.50 0.17 |

Thus, the array becomes `[0.33, 0.67, 1.00, 0.50, 0.17]`.

---
### Merge Two Sorted Arrays into One

### Background — Merge Sort and the Merge Step

### What is Merge Sort?
**Merge Sort** is a classic **divide and conquer algorithm** for sorting arrays.  
It works by repeatedly dividing the array into halves until each half contains one element, then **merging** those sorted halves back together into a single sorted array.

### Conceptual Steps
1. **Divide** the array into two halves.  
2. **Recursively sort** each half.  
3. **Merge** the two sorted halves into one sorted array.

### Why the Merge Step Matters
The **merge step** is where the actual combining happens — it takes two sorted sequences and produces a single sorted sequence efficiently in linear time **O(n)**.  
That’s exactly what this exercise focuses on: merging two pre-sorted arrays `A` and `B` using **pointer traversal** without any additional sorting.

In merge sort:
```
Left half  → already sorted
Right half → already sorted
Merge step → combine both halves in order
```
Example:
```
Left:  [1, 3, 5]
Right: [2, 4, 6]
Merge: [1, 2, 3, 4, 5, 6]
```
This pointer-based merge technique is not only useful for sorting, but also for **combining sorted lists**, **joining results**, or **processing ordered data streams** in systems and algorithms.


### Goal

Write a function:
```c
void merge_sorted(int *A, int n1, int *B, int n2, int *C);
```
that merges **sorted** arrays `A` and `B` into array `C` in ascending order (stable with respect to the original order for equal elements). All arrays are passed as pointers.


### Rules

- **Use pointers only** for traversal — i.e., `int *pA = A; int *pB = B; int *pC = C;` and then dereference/advance.  
  Avoid `A[i]`, `B[i]`, `C[i]` inside `merge_sorted`.  
- Do **not** sort after merging — your merge logic must produce sorted output.  
- Ensure every element from both inputs is written exactly once into `C`.

---

### Starter Code

```c
#include <stdio.h>

void merge_sorted(int *A, int n1, int *B, int n2, int *C);

int main() {
    int n1, n2;
    scanf("%d", &n1);
    int A[n1];
    for (int i = 0; i < n1; i++) scanf("%d", &A[i]);
    scanf("%d", &n2);
    int B[n2];
    for (int i = 0; i < n2; i++) scanf("%d", &B[i]);
    int C[n1 + n2];

    merge_sorted(A, n1, B, n2, C);

    for (int i = 0; i < n1 + n2; i++) printf("%d ", C[i]);
    return 0;
}

void merge_sorted(int *A, int n1, int *B, int n2, int *C) {
    // TODO: implement merging using pointer arithmetic
  
}
```


### Example Input

```
4
1 3 5 7
3
2 4 6
```

### Expected Output

```
1 2 3 4 5 6 7
```


### Extra Test Ideas

| Case | Input (n1, A, n2, B) | Expected Output |
|------|-----------------------|-----------------|
| Equal lengths | 3 → [1 2 3], 3 → [1 2 3] | 1 1 2 2 3 3 |
| Different lengths | 5 → [-3 -1 0 10 12], 2 → [-2 100] | -3 -2 -1 0 10 12 100 |
| One empty array | 4 → [1 2 3 4], 0 → [] | 1 2 3 4 |
| Duplicates & stability | 5 → [2 2 2 5 5], 4 → [2 2 3 5] | 2 2 2 2 2 3 5 5 5 |

---











































# Complicated Exercises (including quizzes from previous semesters)

Credits: Akara Supratak (akara.sup@mahidol.ac.th), Thanpon Noraset (thanapon.nor@mahidol.ac.th), Siripen Pongpaichet (siripen.pon@mahidol.ac.th), and Punyanuch Borwarnginn (punyanuch.bor@mahidol.ac.th)

# Library Book Search 

## Problem Statement
A library stores a collection of book titles. Write a program that searches for books containing a specific keyword (**case-sensitive**). You must implement a function named `containsKeyword` that checks if the keyword exists as a substring of a book title.

---

## Function Definition
You must write the following function:

```c
int containsKeyword(char *title, char *keyword);
```
#### Function Details:

1. Use a manual substring search to check if the keyword exists within title.
2. Use nested loops:
 * Outer loop: Iterate over all possible starting positions in `title`.
 * Inner loop: Compare the characters of `keyword` with the corresponding characters in `title`.
3. Return `1` if a match is found, or `0` if no match is found.

#### Hints for Writing the Function

* Use the `strlen()` function to calculate the lengths of `title` and `keyword`.
* The outer loop should iterate through `title` from index `0` to `(length of title - length of keyword)`.
* The inner loop compares each character of `keyword` with the corresponding characters in `title`. If a mismatch occurs, break out of the loop.
* If all characters of `keyword` match, return `1`. Otherwise, return `0`

## Requirements
1. Read the total number of books (`n`) in the library `(1 ≤ n ≤ 10)`.
2. Read `n` book titles, each up to 50 characters long.
3. Read a single search keyword (up to 50 characters).
4. Use the `containsKeyword` function to determine if each title contains the keyword.
5. Print the matching book titles or "**No Match**" if no books contain the keyword.

### Input Format
* Line 1: An integer `n`, the number of books.
* Next `n` lines: Each line contains a book title.
* Last line: A single keyword to search for.

*Using* `fgets()` *function reads a line of input from the user, including the newline character* (`\n`) *, if space allows. make sure to remove it*

### Output Format
* One matching book title per line (in the same order as input).
* If no book matches, output: **No Match**.





<hr>

**Case 1**:

Sample input:


```text
1
Data Analysis with Python
Python
```

Expected output:

```text
Data Analysis with Python
```

**Case 2**:

Sample input:

```text
3
C++ Basics
Python - A Beginner's Guide
Mastering Java!
Python
```

Expected output:

```text
Python - A Beginner's Guide
```

**Case 3**:

Sample input:

```text
2
JavaScript Essentials
Data Science with Python
Ruby
```

Expected output:

```text
No Match
```

**Case 4**:

Sample input:

```text
2
Java Programming
JavaScript Basics
Java
```

Expected output:

```text
Java Programming
JavaScript Basics
```
