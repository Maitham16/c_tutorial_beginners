# Lesson 11: Functions

## What you will learn

- Why functions help you write cleaner code.
- How to declare, define, and call a function.
- How to pass information into a function and get a result back.
- What function prototypes are and when to use them.

---

## Why use functions?

Imagine you are baking many cakes. Instead of writing the recipe from scratch every time, you write it once and follow it whenever you need it. A function is like a reusable recipe. You write it once, name it, and call it whenever you need that action.

Functions help you:
- Avoid repeating code.
- Break a big problem into smaller pieces.
- Test one piece at a time.
- Make your program easier to read.

---

## A simple function

```c
#include <stdio.h>

void greet() {
    printf("Hello from the function!\n");
}

int main() {
    greet();
    greet();

    return 0;
}
```

Output:

```
Hello from the function!
Hello from the function!
```

The function `greet` does one thing: it prints a message. `main` calls it twice.

---

## Function parts

```c
int add(int a, int b) {
    return a + b;
}
```

| Part            | Meaning                                  |
|-----------------|------------------------------------------|
| `int`           | The return type.                         |
| `add`           | The function name.                       |
| `(int a, int b)`| The parameters it accepts.               |
| `return a + b;` | The value sent back to the caller.       |

The function `add` takes two integers and returns their sum.

---

## Calling a function and using its return value

```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(4, 7);
    printf("4 + 7 = %d\n", result);

    return 0;
}
```

Output:

```
4 + 7 = 11
```

When `main` calls `add(4, 7)`, the values 4 and 7 are copied into `a` and `b`. The function computes the result and sends it back.

---

## Functions that do not return anything

Some functions just perform an action. Their return type is `void`.

```c
#include <stdio.h>

void printLine() {
    printf("----------------\n");
}

int main() {
    printLine();
    printf("Welcome!\n");
    printLine();

    return 0;
}
```

Output:

```
----------------
Welcome!
----------------
```

---

## Function prototypes

In small programs, you can define functions before `main` and everything works. In larger programs, you often want to define them after `main` or in separate files. To do this, you tell the compiler about the function early using a **prototype**.

```c
#include <stdio.h>

// Prototype
int multiply(int x, int y);

int main() {
    int result = multiply(3, 4);
    printf("3 * 4 = %d\n", result);

    return 0;
}

// Definition
int multiply(int x, int y) {
    return x * y;
}
```

Output:

```
3 * 4 = 12
```

The prototype ends with a semicolon. It gives the compiler the function's signature: name, parameter types, and return type.

---

## Common beginner mistakes

- **Forgetting the return type.** Every function must have a return type, even if it is `void`.
- **Mismatching parameters.** If a function expects two `int` values, pass two `int` values.
- **Ignoring the return value.** If a function returns something useful, store or use it.
- **Defining a function inside another function.** In C, functions cannot be nested inside each other.

---

## Mini exercises

1. Write a function `square` that takes an `int` and returns its square.
2. Write a function `isEven` that takes an `int` and returns `1` if it is even, `0` otherwise.
3. Write a function `printHeader` that prints a decorative header and call it before a message.

---

## Recap

- A function is a reusable block of code.
- Functions can take inputs called parameters.
- Functions can return a value using `return`.
- Use `void` when a function does not return anything.
- A prototype declares a function before it is defined.

Functions are one of the most important tools for organizing your programs.