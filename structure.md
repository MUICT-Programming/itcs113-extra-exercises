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
    (*t).a = (*t).b + 3;
}
int main() {
    struct T t = {2, 4};
    modify(&t);
    printf("%d %d", t.a, t.b);
}
```

(Write the exact output.)

<!-- **Answer: 7 4** -->

# Programming Exercise - Problem Solving Question

### 1. Calculate the total price of tickets

Given the starter code below, complete the program to solve this problem.

```c
#include <stdio.h>
#include <string.h>

#define MAX_LENGTH 51

// ===== DO NOT MODIFY =====
struct Person {
  char name[MAX_LENGTH];
  int age;
};
// =========================

struct Ticket {
  // TODO 1: Create Ticket structure (2 lines)
  //
  //// END
};

// ===== DO NOT MODIFY =====
float totalPrice(struct Ticket tickets[], int size) {
  float total = 0.0;
  for (int i = 0; i < size; i++) {
    total += tickets[i].price;
  }
  return total;
}
// =========================

int main() {

  // ===== DO NOT MODIFY =====
  int N;
  float full_price;
  float total_price;
  scanf("%d", &N);
  scanf("%f", &full_price);
  struct Ticket tickets[N]; // Array of tickets
  // =========================

  // TODO 2: Scan to take inputs and assign to each ticket in an array
  //
  //
  //
  //
  //// END

  // TODO 3: call the `totalPrice` function to update the total_price variable
  // (1 line)
  //
  //// END

  // ===== DO NOT MODIFY =====
  for (int i = 0; i < N; i++) {
    printf("[%d] name=%s, age=%d, price=%.2f\n", i, tickets[i].owner.name, tickets[i].owner.age, tickets[i].price);
  }
  printf("Total Price: %.2f", total_price);
  // =========================
}
```

Write a program to calculate the total price when a user wants to purchase tickets. There will be a discount on the full ticket price depending on each ticket owner's age. Please complete the `TODO` tasks in the starter code file.

**TODO 1:** Define a structure `Ticket` with fields `owner` and `price`.

`owner`: a structure of type `"Person"`

`price`: a float value

**TODO 2:** The program should prompt the user to input the number of tickets and the full price, then scan inputs for each ticket owner's `name` and `age`. The ticket's name cannot contain any space (" "). Based on the age, the program should calculate the ticket price. If the `age` is equal to or over 60, the ticket will be half-price (50% off).

**TODO 3:** The program should print the ticket details and the total price of all tickets. To find the total price, you have to call the `totalPrice` function which is already provided.

## Sample Test Cases

### **Case 1**

**Input:**

```
2 15.0
Harry 28
Dumbledore 89
```

**Output:**

```
[0] name=Harry, age=28, price=15.00
[1] name=Dumbledore, age=89, price=7.50
Total Price: 22.50
```

### **Case 2**

**Input:**

```
3 20.0
Mickey 62
Minnie 59
Duffy 12
```

**Output:**

```
[0] name=Mickey, age=62, price=10.00
[1] name=Minnie, age=59, price=20.00
[2] name=Duffy, age=12, price=20.00
Total Price: 50.00
```

### **Case 3**

**Input:**

```
4 315.0
Doraemon 201
Nobita 61
Shizuka 60
Nobisuke 42
```

**Output:**

```
[0] name=Doraemon, age=201, price=157.50
[1] name=Nobita, age=61, price=157.50
[2] name=Shizuka, age=60, price=157.50
[3] name=Nobisuke, age=42, price=315.00
Total Price: 787.50
```

### 2. Count Characters and Words

Given the starter code below, complete the program to solve this problem.

```c
#include <stdio.h>
#include <string.h>

#define MAX_CHAR 420

struct sent_info {
    // TODO 1: Add members of the struct (2 lines)


    //
};

struct sent_info read_sentence(char * out_str) {
    // TODO 2: Add your code here (as many lines as you need)



}

int main() {
    //
    // ===== DO NOT MODIFY =====
    char str[MAX_CHAR];
    struct sent_info info;
    // =========================
    //
    // TODO 3: Add a call to the read_sentence function (1 lines)

    //
    //===== DO NO MODIFY =====
    printf("The sentence is: \"%s\"\n", str);
    printf("The number of characters is %d, and the number of words is %d.\n", info.num_chars, info.num_words);
    return 0;
    // =========================

}

```

Create a function `read_sentence` that has one parameter for an input sentence. The function reads an input sentence from the command line into the input parameter and returns the following data via a struct:

`num_chars`: Number of characters (not including `'\0'` or `'\n'`)

`num_words`: Number of words (only spaces separate words)
The function prototype of the `read_sentence` is as follows:

```
struct sent_info read_sentence(char * out_str);
```

Please be careful about the following:

- `'\0'` or `'\n'` end the sentence.
- Two words can be separated by more than one space. See the example below.
- Spaces might start or end the sentence.

### **Example 1**

**Input (there is a space before and after):**

```
 xy
```

**Output:**

```
The sentence is: " xy "
The number of characters is 4, and the number of words is 1.
```

### **Example 2**

**Input:**

```
the answer is 42.
```

**Output:**

```
The sentence is: "the answer is 42."
The number of characters is 17, and the number of words is 4.
```

### **Example 3**

**Input (there is a space after and two spaces between cc, ee, and xx):**

```
Aa bb cc  ee  xx yy
```

**Output:**

```
The sentence is: "Aa bb cc  ee  xx yy "
The number of characters is 20, and the number of words is 6.
```

### 3. Computing GPA and Student Status

Given the starter code below, complete the program to solve this problem.

```c
#include <stdio.h>
#include <string.h>

#define MAX_LINE_LEN 150
#define MAX_COURSE_LEN 120
#define MAX_STATUS_LEN 10
#define N_GRADES 8
#define MAX_ENROLL 7

char POSSIBLE_GRADES[N_GRADES][3] = {"A", "B+", "B", "C+", "C", "D+", "D", "F"};


struct Course {
    // TODO 1: Declare a structure for the course enrollment


    // END 1
};

int convert_char_to_int(char c, int *out);
int convert_str_to_grade(char str[], float *out);
void parse_course(char line[], char *course_id, char *course_name, int *credit, float *grade);

// TODO 2: Create two function prototypes for the functions:
//         - create_course
//         - compute_gpa


// END 2

int main() {
    int n = 0;
    char status[MAX_STATUS_LEN];
    float gpa;
    struct Course courses[MAX_ENROLL];
    char line[MAX_LINE_LEN];
    while (fgets(line, MAX_LINE_LEN, stdin) != NULL) {
        if (strlen(line) <= 1) { break; }
        courses[n] = create_course(line);
        n++;
    }

    gpa = compute_gpa(courses, n, status);

    printf("================== Enrollment ==================\n");
    for (int i = 0; i < n; i++) {
        struct Course c = courses[i];
        printf(
            "%s %s %d %.2f\n",
            // TODO 3: Add Course ID, Course Name, Course Credit, and Course Grade


            // END 3
            );
    }
    printf("------------------------------------------------\n");
    printf("GPA: %.2f\nSTATUS: %s\n", gpa, status);
    printf("================================================\n");
    return 0;
}


int convert_char_to_int(char c, int *out) {
    if (c >= '0' && c <= '9') {
        *out = c - '0';
        return 1;
    } else {
        *out = -1;
        return 0;
    }
}

int convert_str_to_grade(char str[], float *out) {
    float grade = 4.0;
    for (int i = 0; i < N_GRADES; i++) {
        if(strcmp(str, POSSIBLE_GRADES[i]) == 0) {
            *out = grade;
            return 1;
        }
        grade -= 0.5;
        if (grade == 0.5) {
            grade = 0.0;
        }
    }
    return 0;
}


void parse_course(char line[], char *course_id, char *course_name, int *credit, float *grade) {
    int state = 0, j = 0;
    char grade_str[3];
    for (int i = 0; (line[i] != '\0' && line[i] != '\n'); i++) {
        if (line[i] == ',') {
            state++;
            j = 0;
            continue;
        }
        switch (state) {
        case 0:
            course_id[j] = line[i];
            course_id[j+1] = '\0';
            break;
        case 1:
            course_name[j] = line[i];
            course_name[j+1] = '\0';
            break;
        case 2:
            convert_char_to_int(line[i], credit);
            break;
        case 3:
            grade_str[j] = line[i];
            grade_str[j+1] = '\0';
            break;
        default:
            break;
        }
        j++;
    }
    convert_str_to_grade(grade_str, grade);
}

// TODO 4: Define the function create_course
//         This function must call `parse_course`


// END 4

// TODO 5: Define the function compute_gpa


// END 5


```

## Background

A student takes many courses per semester. The GPA of a semester can be computed from the sum of subject credits multiply by grade point and then divided by total credits. For example, if a student enrolls and gets grades:

- ITCS113,Fundamentals of Programming,3,A
- ITLG111,Technical English I,2,B
- ITCS111,Linear Algebra and Calculus for Computing,3,B+

This student will get GPA of

```plaintext
((3 x 4.0) + (2 * 3.0) + (3 * 3.5)) / 8 = 3.56
```

\*used only two decimal places

The status of a student depends on the GPA, following the rules below:

- GPA >= 2.0, Status: `"NORMAL"`
- GPA >= 1.8 and GPA < 2.0, Status: `"PRO 2"`
- GPA >= 1.5 and GPA < 1.8, Status: `"PRO 1"`
- GPA < 1.5, Status: `"RETIRED"`

## Instruction

This question has five parts. You should first read the overall code in the main.c and then start writing your code one part at a time.

1. [TODO 1, 1 pt] Declare a structure name `Course`. A course consists of
   - Course ID (e.g., `"ITCS113"`)
   - Course Name (e.g., `"Fundamentals of Programming"`)
   - Credit (e.g., `3`)
   - Grade Point (e.g., `3.5` - if the letter grade is `B`)
2. [TODO 2, 1 pt] Declare two function _prototypes_:

   - `create_course` takes a string in the CSV format and return the structure course. An example of a function call is

     ```c
     struct Course c = create_course("ITCS113,Fundamental of Programming,3,B+");
     ```

   - `compute_gpa` takes an array of courses, number of courses, and status string; and return the GAP. Additionally, set the status string. An example of a function call is

     ```c
     int n = 7;
     char status[10];
     struct Course courses[n] = {...};  // init the courses

     gpa = compute_gpa(courses, n, status);
     ```

3. [TODO 3, 1 pt] Print the course ID, course name, credit, and grade point.
4. [TODO 4, 4 pt] Define the function `create_course` (declare in TODO 2). We will assume that the string argument always has the correct formatting. An example of a function call is

   ```c
   struct Course c = create_course("ITCS113,Fundamental of Programming,3,B+");
   // c will contain the following information
   // Course ID: "ITCS113"
   // Course Name: "Fundamentals of Programming"
   // Credit: 3
   // Grade: 3.5
   ```

   To help you process this, we defined a helper function for you.

   ```c
   void parse_course(char line[], char *course_id, char *course_name, int *credit, float *grade);
   ```

   This function converts a string `line` into the course ID, course name, credit, and grade; and sets them into the pointers: `course_id`, `course_name`, `credit`, and `grade` respectively.

   Calling this function correctly will give you 1 point.

5. [TODO 5, 3 pt] Define the function `compute_gpa` (declare in TODO 2). An example of a function call is

   ```c
   int n = 3;
   char status[10];
   struct Course courses[] = {
       {"ITCS113","Fundamentals of Programming",3,2.0},
       {"ITLG111","Technical English I",2,1.5}
   }

   float gpa = compute_gpa(courses, n, status);
   // gpa is 1.80
   // status is "PRO 2"
   ```

## Example Cases

### Case 1

**Inputs (ends with an empty line):**

```plaintext
ITCS113,Fundamentals of Programming,3,A
ITLG111,Technical English I,2,B
ITCS111,Linear Algebra and Calculus for Computing,3,B+

```

**Expected outputs (ends with a new line):**

```plaintext
================== Enrollment ==================
ITCS113 Fundamentals of Programming 3 4.00
ITLG111 Technical English I 2 3.00
ITCS111 Linear Algebra and Calculus for Computing 3 3.50
------------------------------------------------
GPA: 3.56
STATUS: NORMAL
================================================

```

### Case 2

**Inputs (ends with an empty line):**

```plaintext
ITCS113,Fundamentals of Programming,3,D+

```

**Expected outputs (ends with a new line):**

```plaintext
================== Enrollment ==================
ITCS113 Fundamentals of Programming 3 1.50
------------------------------------------------
GPA: 1.50
STATUS: PRO 1
================================================

```

### Case 3

**Inputs (ends with an empty line):**

```plaintext
ITCS113,Fundamentals of Programming,3,D
ITLG111,Technical English I,2,F
ITCS111,Linear Algebra and Calculus for Computing,3,D+
ITCS112,Discrete Structures,3,D+
ITCS114,Introduction to Computer Ethics,1,C+

```

**Expected outputs (ends with a new line):**

```plaintext
================== Enrollment ==================
ITCS113 Fundamentals of Programming 3 1.00
ITLG111 Technical English I 2 0.00
ITCS111 Linear Algebra and Calculus for Computing 3 1.50
ITCS112 Discrete Structures 3 1.50
ITCS114 Introduction to Computer Ethics 1 2.50
------------------------------------------------
GPA: 1.21
STATUS: RETIRED
================================================

```

