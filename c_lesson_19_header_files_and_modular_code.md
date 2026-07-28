# Lesson 19: Header Files and Modular Code

## What you will learn

- Why splitting code into multiple files is useful.
- How to use `#include` to share declarations.
- What header files are and how to write them.
- How to use header guards to prevent errors.
- How to compile a multi-file project.

---

## Why split your code?

As programs grow, putting everything into one file becomes messy. Splitting code into multiple files makes it easier to:

- Find what you are looking for.
- Reuse code in other projects.
- Work on different parts with other people.
- Fix bugs without touching unrelated code.

A good split is to put reusable functions in their own file and share their declarations through a header file.

---

## An example project structure

Imagine you want to create a small math helper library.

```
project/
  main.c
  math_utils.c
  math_utils.h
```

- `math_utils.h` contains the function prototypes.
- `math_utils.c` contains the function definitions.
- `main.c` uses the functions.

---

## The header file

A header file declares what is available. It does not contain the full code, just the promises.

```c
// math_utils.h
#ifndef MATH_UTILS_H
#define MATH_UTILS_H

int add(int a, int b);
int multiply(int a, int b);

#endif
```

The `#ifndef`, `#define`, and `#endif` lines form a **header guard**. They prevent the same header from being included more than once in the same file. Without the guard, you could get errors from duplicate declarations.

---

## The source file

The source file contains the actual implementations.

```c
// math_utils.c
#include "math_utils.h"

int add(int a, int b) {
    return a + b;
}

int multiply(int a, int b) {
    return a * b;
}
```

Notice the quotes around `math_utils.h`. Quoted includes tell the compiler to look in the current directory first. Angle brackets like `<stdio.h>` are used for system libraries.

---

## The main file

```c
// main.c
#include <stdio.h>
#include "math_utils.h"

int main() {
    int x = 4;
    int y = 5;

    printf("%d + %d = %d\n", x, y, add(x, y));
    printf("%d * %d = %d\n", x, y, multiply(x, y));

    return 0;
}
```

---

## Compiling a multi-file program

If you are using an online compiler, some do not support multiple files. In that case, you can paste all files into a single editor window, but this is less realistic.

On your own computer with `gcc`, you compile all the `.c` files together:

```bash
gcc main.c math_utils.c -o myprogram
```

This tells the compiler to combine the files into one executable called `myprogram`.

---

## What belongs in a header file?

Put these in header files:
- Function prototypes.
- Structure definitions.
- Constant definitions with `#define`.
- Type aliases with `typedef`.

Do not put these in header files:
- Full function definitions, unless they are very small `static inline` helpers.
- Variable definitions that should not be shared globally.

---

## Common beginner mistakes

- **Forgetting header guards.** This can cause duplicate definition errors.
- **Defining functions in headers without special handling.** Include only declarations.
- **Using angle brackets for your own headers.** Use quotes for project headers.
- **Not compiling all `.c` files together.** If you forget `math_utils.c`, the linker cannot find the function bodies.

---

## Mini exercises

1. Create a `greetings.h` and `greetings.c` that declare and define a `sayHello` function. Call it from `main.c`.
2. Add a header guard to your header file and explain why it is needed.
3. Compile your project by listing all `.c` files on the command line.

---

## Recap

- Split programs into `.c` source files and `.h` header files.
- Headers contain declarations to share between files.
- Source files contain the actual implementations.
- Use header guards to avoid duplicate inclusions.
- Compile all `.c` files together with `gcc`.

Modular code is the first step toward writing professional, maintainable programs.