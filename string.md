# Extra Exercise: String in C

Credits: Siripen Pongpaichet (email: siripen.pon@mahidol.ac.th)

# Initializing a string

### **Which of the following correctly represents a string in C?**

- [ ] A. `'Hello'`
- [ ] B. `"Hello"`
- [ ] C. `Hello`
- [ ] D. `char greeting;`

<!-- **Answer:** B -->

---

### **What is the main difference between `'A'` and `"A"` in C?**

- [ ] A. `'A'` is a string, `"A"` is a character
- [ ] B. Both are strings
- [ ] C. `'A'` is a character, `"A"` is a string
- [ ] D. Both are characters

<!-- **Answer:** C  -->

---

### **Which declaration correctly initializes a _modifiable_ string in C?**

- [ ] A. `char *str = "Hello";`
- [ ] B. `char str[] = "Hello";`
- [ ] C. `string str = "Hello";`
- [ ] D. `char str = {'H','e','l','l','o'};`

<!-- **Answer:** B  -->

---

### **What happens if you attempt to modify a string literal defined as:**

```c
char *date = "June 14";
date[0] = 'A';
```

- [ ] A. It modifies the string successfully
- [ ] B. It causes a runtime error
- [ ] C. It compiles but gives a warning
- [ ] D. It truncates the string

<!-- **Answer:** B  -->

---

# String Input and Output Functions

### **Which input function in C _stops reading at the first whitespace_?**

- [ ] A. `scanf("%s", str);`
- [ ] B. `fgets(str, n, stdin);`
- [ ] C. `getchar();`
- [ ] D. `puts(str);`

<!-- **Answer:** A  -->

---

### **When using `fgets(str, n, stdin);`, what happens if the input string is shorter than `n-1`?**

- [ ] A. It removes the newline character automatically
- [ ] B. It keeps the newline character
- [ ] C. It causes an error
- [ ] D. It adds two null terminators

## <!-- **Answer:** B  -->

### **What is the purpose of the following code?**

```c
if ((pos = strchr(input_str, '\n')) != NULL)
    *pos = '\0';
```

- [ ] A. Removes the null terminator
- [ ] B. Converts `\n` to a space
- [ ] C. Removes the newline character from the string
- [ ] D. Adds a newline character to the string

<!-- **Answer:** C  -->

---

### **`scanf("%s", str);` automatically stops reading input when a space or newline character is encountered.** (True or False)

**Answer:** ******\_\_******

<!-- **Answer:** True  -->

---

### **Which of the following statements about `getchar()` is TRUE?**

- [ ] A. It reads one character at a time from standard input.
- [ ] B. It reads a full line including spaces.
- [ ] C. It reads until EOF and returns a string.
- [ ] D. It automatically skips whitespace.

<!-- **Answer:** A  -->

---

# String Library Function

### **Which string function is used to **compare** two strings in C?**

- [ ] A. `strcmp(str1, str2)`
- [ ] B. `strcat(str1, str2)`
- [ ] C. `strlen(str1)`
- [ ] D. `strcpy(str1, str2)`

<!-- **Answer:** A  -->

---

### **What will `strlen("Hello")` return?**

- [ ] A. 4
- [ ] B. 5
- [ ] C. 6
- [ ] D. Undefined

<!--  **Answer:** B  -->

---

### **What will the following code print?**

```c
char s1[20] = "Hello";
char s2[20] = "World";
strcat(s1, s2);
printf("%s", s1);
```

- [ ] Hello World
- [ ] HelloWorld
- [ ] WorldHello
- [ ] Hello

## <!--  **Answer:** B  -->

### **What value will strcmp("Cat", "Car") return — positive, negative, or zero — and why?**

**Answer:**

<!-- **Answer:** Returns a positive value because `'t'` > `'r'` in ASCII order. -->
---

# Loop through String

### **Given the code below, what will be printed?**

```c
char str[] = "Learning_C_is_fun!";
int i = 0;
while (str[i] != '\0') {
    if (str[i] == '_') str[i] = ' ';
    i++;
}
printf("%s", str);
```

- [ ] A. `Learning_C_is_fun!`
- [ ] B. `Learning C is fun!`
- [ ] C. `Learning C_is_fun!`
- [ ] D. Compilation error

<!-- **Answer:** B  -->

---

# Fill in the code

### **Without using `strcpy()`, fill in the missing code to manually copy `src` into `dest`.**

```c
#include <stdio.h>

int main() {
    char src[] = "C Programming";
    char dest[50];
    int i = 0;

    while (__________ && i < 49) {     // <--- fill condition
        dest[i] = src[i];
        i++;
    }
    dest[i] = '\0';
    printf("Copied string: %s", dest);
    return 0;
}
```

<!-- **Answer:** `src[i] != '\0'`  -->

---

### **Fill in the missing code to count how many digits (`'0'–'9'`) are in the given string using `<ctype.h>` functions.**

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>

int main() {
    char str[] = "CS113 has 3 exams and 1 project.";
    int count = 0;

    for (int i = 0; i < __________; i++) {    // <--- fill here
        if (__________(str[i]))               // <--- fill here
            count++;
    }

    printf("Total digits: %d", count);
    return 0;
}

```

<!-- **Answer:**
* `strlen(str)`
* `isdigit`
-->

---

### **Complete the code to replace all spaces `' '` in a given string with underscores `'_'`.**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "Data Science with C Language";
    int i = 0;

    while (__________) {                  // <--- fill here
        if (str[i] == ' ')
            __________;                   // <--- fill here
        i++;
    }

    printf("%s", str);
    return 0;
}

```

<!-- **Answer:**
* Condition -> `str[i] != '\0'`
* Replacement -> `str[i] = '_'`
-->

---

# Programming Exercise - Problem Solving Question

### 1. Find the Word with the Highest Order

Given the starter code below, complete the program to solve this problem.

```c
#include <stdio.h>
#include <string.h>

#define MAX_LENGTH 50

int main() {
  printf("Enter list of words (or 'quite' to exit)\n");
  char maxWord[MAX_LENGTH]; // This maxWord is used to keep the highest order

  ///// Start your code here /////
  /////
  ///// End your code here /////

  printf("Word with the highest order is: %s", maxWord);
  return 0;
}
```

Write a **C program** that receives multiple strings until the word `"quit"` is entered.

Once `"quit"` is entered, the program will determine **the word with the highest order in alphabetical order** and display it.

> **Definition:**  
> The word with the _highest order_ is the one that comes **last** when all words are arranged in **ascending ASCII order**.
>
> For example, given the words `"Three"`, `"Two"`, and `"one"`:
>
> - `"Two"` comes after `"Three"` because `'w'` (in "Two") has a higher ASCII value than `'h'` (in "Three").
> - `"one"` comes after `"Two"` because `'o'` (in "one") has a higher ASCII value than `'T'` (in "Two").
>
> Therefore, `"one"` has the highest order.

## Instructions

1. Use a **while loop** to continually prompt the user for words **until `"quit"` is entered**.
2. Assume the **maximum length of a word is 50 characters** (not including `'\0'`).
3. Use **string comparison functions** (e.g., `strcmp`) to find the word that comes last alphabetically.
   - Keep track of the current highest word in a variable named `maxWord`.
4. When `"quit"` is entered, **display the word with the highest order**.

> Each input is a _single word_ (no spaces).  
> For example:  
> If the user enters `at least one`, it will be treated as **three words**: `at`, `least`, and `one`.

## Restrictions

- You **must not modify** any other part of the starter code except the sections marked for editing.
- Failure to follow this instruction will result in a **zero score**.

## Sample Test Cases

### **Case 1**

**Input:**

```
apple
banana
orange
quit
```

**Output:**

```
Word with the highest order is: orange
```

### **Case 2**

**Input:**

```
Quiz_is_easy
Hello_world
you_can_make_it
quit
```

**Output:**

```
Word with the highest order is: you_can_make_it
```

### **Case 3**

**Input:**

```
at least one
quit
```

**Output:**

```
Word with the highest order is: one
```

### **Case 4**

**Input:**

```
quit
again
quit
```

**Output:**

```
Word with the highest order is: quit
```

---

### 2. Reverse Each Word

Write a **C program** that reads a sentence (up to 100 characters) and prints each word **reversed**, but the **word order remains the same**.

> Example:  
> `"Hello World"` -> `"olleH dlroW"`

## Instructions

1. Read the full line using `fgets()`.
2. Use a loop to traverse the string character by character.
3. Identify words separated by spaces.
4. Reverse each word **in place** or using a temporary array.
5. Print the modified string.

## Notes

- Use `strlen()` to determine word length.
- Handle both uppercase and lowercase characters.
- Assume input contains only letters and spaces.

## Sample Test Cases

### **Case 1**

**Input:**

```
Mahidol University
```

**Output:**

```
lodihaM ytisrevinU
```

### **Case 2**

**Input:**

```
C Programming is FUN
```

**Output:**

```
C gnimmargorP si NUF
```

### **Case 3**

**Input:**

```
MoM RefeR RotatoR WoW
```

**Output:**

```
MoM RefeR RotatoR WoW
```

---

### 3. Count Vowels and Consonants

Write a **C program** that reads a sentence (up to 100 characters) and counts the number of **vowels** and **consonants** in it.

> Example:  
> `"Hello World"` -> Vowels: 3, Consonants: 7

## Instructions

1. Read the input sentence using `fgets()`.
2. Traverse each character in the string using a loop.
3. Use functions from `<ctype.h>` such as `isalpha()` and `tolower()`.
4. Count:
   - **Vowels:** `'a'`, `'e'`, `'i'`, `'o'`, `'u'`
   - **Consonants:** all other letters
5. Print both counts.

## Notes

- Ignore digits, spaces, and punctuation.
- Handle both **uppercase and lowercase** letters.

## Sample Test Cases

### **Case 1**

**Input:**

```
@Mahidol University@
```

**Output:**

```
Vowels: 7
Consonants: 10
```

### **Case 2**

**Input:**

```
Programming in C is Fun!
```

**Output:**

```
Vowels: 6
Consonants: 11
```

### **Case 3**

**Input:**

```
### What is the value of (1+2)*(2+3)*(3+4) ###
```

**Output:**

```
Vowels: 7
Consonants: 9
```

---
