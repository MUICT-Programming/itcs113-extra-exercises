# Extra Exercises: Discord Discard (Loops, Conditionals, Characters)

Credits: Poonyawatt Klumnaim (email: poon@pnwttklm.com, github: [@pnwttklm](https://github.com/pnwttklm))

---

# D: Discord Discard

Jack is a developer at Discord. The feedback from executives said that there are too many improper words in Discord and they want you to decrease them.

In order to solve the problem, your intelligent gut thinks that you gonna let user type the number which is length of the characters that user want to type. Then get a character that will be banned e.g., `'n'`. After that, let user type characters — if the user does not type that character it will print character by character right away. If the user types the banned character, the program will skip printing that character.

## Input Format

- An integer `n` — length of characters
- A character `x` — banned character
- Characters `c1, c2, c3, ... cn`

## Constraints

-

## Output Format

Characters that are not the banned character.

## Sample Input 0

```
7
z
z
a
b
z
c
d
z
```

## Sample Output 0

```
abcd
```

## Sample Input 1

```
5
n
N
n
a
N
b
```

## Sample Output 1

```
NaNb
```

### Explanation 1

The banned character is lowercase `'n'`. Uppercase `'N'` is a different character, so it is not filtered out.

## Sample Input 2

```
7
!
H
e
l
l
o
!
!
```

## Sample Output 2

```
Hello
```
