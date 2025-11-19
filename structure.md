# Extra Exercise: Structures in C

### 1. What is a structure in C?

- [ ] A. A built-in data type that stores only integers
- [ ] B. A user-defined data type that can group variables of different types
- [ ] C. A function that allocates memory
- [ ] D. A pointer to multiple arrays

<!-- **Answer: B** -->

### 2. Which syntax correctly declares a structure named `Date`?

- [ ] A. `date struct { int day; int month; int year; };`
- [ ] B. `struct Date { int day; int month; int year; };`
- [ ] C. `struct { int day; int month; int year; } Date;`
- [ ] D. `Date struct { day, month, year };`

<!-- **Answer: B** -->

### 3. How do you access member `x` of structure variable `p1`?

- [ ] A. `p1-\>x`
- [ ] B. `x.p1`
- [ ] C. `p1.x`
- [ ] D. `p1(x)`

<!-- **Answer: C** -->

### 4. Which statement initializes a structure correctly?

- [ ] A. `struct Point p = (1,2);`
- [ ] B. `Point p = {1,2};`
- [ ] C. `struct Point p = {1,2};`
- [ ] D. `struct Point p; p = {1,2};`

<!-- **Answer: C** -->

### 5. Which of the following correctly copies one structure variable to another?

- [ ] A. `struct1.copy(struct2);`
- [ ] B. `struct1 == struct2;`
- [ ] C. `struct1 = struct2;`
- [ ] D. `copy(struct1, struct2);`

<!-- **Answer: C** -->

### 6. Given a structure containing a char array, which function is commonly used to copy a string into it?

- [ ] A. `strpaste()`
- [ ] B. `strcopy()`
- [ ] C. `strcpy()`
- [ ] D. `string_copy()`

<!-- **Answer: C** -->

### 7. What is the correct way to declare an array of 20 structures named `Item`?

- [ ] A. `Item items(20);`
- [ ] B. `struct Item items\[20\];`
- [ ] C. `struct items\[20\] Item;`
- [ ] D. `array Item\[20\];`

<!-- **Answer: B** -->

### 8. What does the following code represent?

typedef struct Date DATE;

- \[ \] A. It creates a new structure called `DATE`
- \[ \] B. It deletes the `struct Date` type
- \[ \] C. It assigns a short alias `DATE` for `struct Date`
- \[ \] D. It converts `DATE` into an integer type

<!-- **Answer: C** -->

### 9. In a struct-in-struct declaration, which is valid?

- [ ] A. Using a structure before it is declared
- [ ] B. A structure cannot contain another structure
- [ ] C. A structure can contain another structure as a member
- [ ] D. Inner structure must appear after main struct

<!-- **Answer: C** -->

### 10. Which function prototype correctly passes a struct as a parameter?

- [ ] A. `float calDist(Point p1, p2);`
- [ ] B. `float calDist(struct Point p1, struct Point p2);`
- [ ] C. `float calDist(struct p1, struct p2);`
- [ ] D. `float calDist(struct Point\* p1, p2);`

<!-- **Answer: B** -->

### 11. Which of the following correctly passes a structure **by reference** to a function?

- [ ] A. `foo(struct Point p);`
- [ ] B. `foo(Point p);`
- [ ] C. `foo(struct Point *p);`
- [ ] D. `foo(*Point p);`

<!-- **Answer: C** -->

### 12. Given the code:

```c
struct Data { int a; int b; };
struct Data d1 = {10, 20};
struct Data d2 = d1;
d2.a = 99;
```

What are the values of `d1.a` and `d2.a`?

- \[ \] A. `10`, `10`
- \[ \] B. `99`, `99`
- \[ \] C. `10`, `99`
- \[ \] D. `99`, `10`

<!-- **Answer: C** -->

### 13. What is the output?

```c
#include <stdio.h>

struct P
{
    int x;
    int y;
};

int main()
{
    struct P p = {3, 4};
    struct P *ptr = &p;
    (*ptr).x += 2;

    printf("%d %d", p.x, p.y);
}
```

- [ ] A. `3 4`
- [ ] B. `5 4`
- [ ] C. `3 6`
- [ ] D. Compile error

<!-- **Answer: B** -->

### 14. Which is the correct way to initialize a struct containing another struct?

```c
struct Date { int d, m, y; };
struct Item { int id; struct Date restock; };
```

- [ ] A. `struct Item it = {1, 1, 1, 2020};`
- [ ] B. `struct Item it = {1, {1, 1, 2020}};`
- [ ] C. `struct Item it = {{1, 1, 2020}, 1};`
- [ ] D. `struct Item it = (1, {1,1,2020});`

<!-- **Answer: B** -->

### 15. Consider:

```c
struct Student
{
    int id;
    char name[20];
};

typedef struct Student STUDENT;

main()
{

    STUDENT s1 = {1, "Alice"};
}

```

What is true?

- \[ \] A. `typedef` creates a pointer-only alias\
- \[ \] B. `STUDENT` is now equivalent to `struct Student`\
- \[ \] C. `STUDENT` is a new type alias for the anonymous struct\
- \[ \] D. `Student` is a new type alias for the anonymous struct\

<!-- **Answer: B** -->

### 16. What is the output?

```c
struct A {
    int x;
};

void update(struct A a)
{
    a.x += 5;
}

int main() {
    struct A a = {10};
    update(a);
    printf("%d", a.x);
}
```

- [ ] A. `10`
- [ ] B. `15`
- [ ] C. Undefined
- [ ] D. Compile error

<!-- **Answer: A** -->

### 17. Which code snippet correctly returns a struct?

- [ ] A.

```c
struct P foo() {
    struct P p;
    p.x = 1;
    return p;
}
```

- [ ] B.

```c
P foo() { return (1,2); }
```

- [ ] C.

```c
foo(struct P p) { return p; }
```

- [ ] D.

```c
struct P foo(struct P p);
```

<!-- **Answer: A** -->

### 18. Consider:

```c
struct Node {
    int value;
    struct Node *next;
};
```

What does this represent?

- \[ \] A. A self-referencing structure used for linked lists\
- \[ \] B. A multidimensional array\
- \[ \] C. A function pointer\
- \[ \] D. A union type
<!-- **Answer: A** -->

### 19. Short Answer

Write a statement to assign the value `30` to the `qty` field of the 4th element in an array `items` of type `struct Item`.

<!-- **Answer: items[3].qty = 30;** -->

### 20. Coding Output

What is the output?

```c
struct T { int a; int b; };
void modify(struct T *t) {
    t->a = t->b + 3;
}
int main() {
    struct T t = {2, 4};
    modify(&t);
    printf("%d %d", t.a, t.b);
}
```

(Write the exact output.)
