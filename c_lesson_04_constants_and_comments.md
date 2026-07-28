# Lesson 4: Constants and Comments

## What you will learn

- How to write notes inside your code with comments.
- How to create values that never change: constants.
- Why constants make your code safer and easier to read.
- When to comment and when to let the code speak for itself.

---

## Why comment your code?

Programs are read by two audiences: the computer and humans. The computer ignores comments, but humans, including your future self, rely on them to understand why the code exists.

Good comments explain intent. Bad comments repeat what the code already says.

For example, this comment is useless:

```c
int x = 5; // set x to 5
```

This comment is useful:

```c
int maxAttempts = 5; // limit chosen to prevent brute-force attacks
```

---

## Two kinds of comments

### Single-line comments

Use `//` for comments that fit on one line.

```c
// This program greets the user
#include <stdio.h>

int main() {
    printf("Hello!\n"); // print a greeting
    return 0;
}
```

### Multi-line comments

Use `/* */` for longer comments that span multiple lines.

```c
/*
    Author: Your Name
    Purpose: Show how comments work
    Date: 2026
*/

#include <stdio.h>

int main() {
    printf("Comments are helpful!\n");
    return 0;
}
```

Multi-line comments can also sit at the end of a line:

```c
int value = 100; /* temporary default */
```

---

## Constants

A constant is a value that must not change while the program runs. If you try to change it, the compiler stops you.

There are two common ways to make constants in C.

### Using `#define`

`#define` is a preprocessor directive. It tells the compiler to replace one piece of text with another before the program is compiled.

```c
#include <stdio.h>

#define PI 3.14159

int main() {
    printf("The value of PI is %f\n", PI);
    return 0;
}
```

Output:

```
The value of PI is 3.141590
```

`PI` has no type and no semicolon. It is not a variable. It is a textual replacement. Everywhere the compiler sees `PI`, it substitutes `3.14159`.

### Using `const`

`const` creates a real variable that cannot be modified.

```c
#include <stdio.h>

int main() {
    const int maxScore = 100;
    printf("Maximum score: %d\n", maxScore);
    return 0;
}
```

Output:

```
Maximum score: 100
```

If you try to change `maxScore`, the compiler will report an error.

---

## Which one should you use?

Both work, but they feel slightly different.

- Use `#define` for simple, typeless values that are used in many places, like `PI` or `MAX_SIZE`.
- Use `const` when you want a typed value with memory, especially inside functions.

As a beginner, either is fine. The important thing is that you avoid scattering magic numbers like `3.14159` or `100` throughout your code without a name.

---

## A complete example

```c
#include <stdio.h>

#define PI 3.14159

int main() {
    const int radius = 5;
    double area = PI * radius * radius;

    printf("Radius: %d\n", radius);
    printf("Area of circle: %f\n", area);

    return 0;
}
```

Output:

```
Radius: 5
Area of circle: 78.539750
```

Here `radius` is a `const int`, so it cannot accidentally change. `PI` is a named constant defined once and reused.

---

## Common beginner mistakes

- **Putting a semicolon after `#define`.** `#define PI 3.14;` will replace `PI` with `3.14;`, which can break expressions.
- **Trying to change a `const` variable.** The whole point is that it stays the same.
- **Writing comments that explain the obvious.** Comments should add meaning, not noise.
- **Forgetting to close a multi-line comment.** Everything after an unclosed `/*` becomes part of the comment.

---

## Mini exercises

1. Add a single-line comment at the top of a program explaining what it does.
2. Define a constant for the number of days in a week using `#define`. Print it.
3. Create a `const float` for your height and try to change it. What does the compiler say?

---

## Recap

- Comments are notes for humans. The compiler ignores them.
- Use `//` for one line and `/* */` for multiple lines.
- Constants are values that should not change.
- `#define` creates a text replacement constant.
- `const` creates a typed, read-only variable.
- Name important values instead of leaving magic numbers in your code.

Good comments and named constants make your code readable and trustworthy.