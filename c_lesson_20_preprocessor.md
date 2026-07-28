# Lesson 20: The Preprocessor

## What you will learn

- What the preprocessor does before the compiler runs.
- How to use `#include`, `#define`, and macros.
- How conditional compilation works.
- Why macros can be useful and dangerous.

---

## What is the preprocessor?

Before your C code is compiled, a tool called the **preprocessor** runs. It looks at lines that start with `#` and performs simple text replacements and file inclusions.

The result is a single long file that is then passed to the compiler.

---

## `#include`

`#include` copies the contents of another file into your source file. You have been using this all along.

```c
#include <stdio.h>
```

This copies the standard input/output header into your file so the compiler knows about `printf` and `scanf`.

```c
#include "my_header.h"
```

This copies your own header file into the current source file.

---

## `#define` for constants

`#define` creates a textual replacement. Before compilation, every occurrence of the macro name is replaced with its value.

```c
#include <stdio.h>

#define PI 3.14159

int main() {
    printf("PI is %f\n", PI);
    return 0;
}
```

Output:

```
PI is 3.141590
```

After preprocessing, the line inside `main` looks like:

```c
printf("PI is %f\n", 3.14159);
```

There is no variable called `PI`. It is just text substitution.

---

## Macros with arguments

Macros can take arguments, which makes them look like functions but work like text replacement.

```c
#include <stdio.h>

#define SQUARE(x) ((x) * (x))

int main() {
    printf("Square of 5: %d\n", SQUARE(5));
    printf("Square of 3+2: %d\n", SQUARE(3 + 2));

    return 0;
}
```

Output:

```
Square of 5: 25
Square of 3+2: 25
```

The parentheses around `x` are important. Without them, `SQUARE(3 + 2)` could expand incorrectly because of operator precedence.

Compare this wrong version:

```c
#define SQUARE(x) x * x
```

Then `SQUARE(3 + 2)` becomes `3 + 2 * 3 + 2`, which is `11`, not `25`. Always use parentheses around macro arguments.

---

## Conditional compilation

You can tell the preprocessor to include or skip parts of your code based on conditions.

```c
#include <stdio.h>

#define DEBUG 1

int main() {
    #if DEBUG
        printf("Debug mode is on.\n");
    #else
        printf("Debug mode is off.\n");
    #endif

    return 0;
}
```

Output:

```
Debug mode is on.
```

If you change `#define DEBUG 1` to `#define DEBUG 0`, the other branch is compiled.

This is useful for including debug prints only during development.

---

## `#ifdef` and `#ifndef`

`#ifdef` checks if a macro is defined. `#ifndef` checks if it is not defined. These are often used for header guards.

```c
#ifndef MY_HEADER_H
#define MY_HEADER_H

// declarations here

#endif
```

If `MY_HEADER_H` is already defined, the preprocessor skips the entire block. This prevents the same declarations from being included twice.

---

## Common beginner mistakes

- **Putting a semicolon after `#define`.** `#define PI 3.14;` causes unexpected replacements.
- **Forgetting parentheses in macros.** This leads to operator precedence bugs.
- **Using macros when a function is better.** Functions are safer, easier to debug, and respect types.
- **Defining constants in headers without header guards.** This can cause redefinition errors.

---

## Mini exercises

1. Define a macro `MAX(a, b)` that returns the larger of two values. Test it carefully with parentheses.
2. Use `#ifdef` to include a debug print only when a `DEBUG` macro is defined.
3. Explain why header guards use `#ifndef` instead of `#ifdef`.

---

## Recap

- The preprocessor runs before the compiler.
- `#include` copies file contents into your source.
- `#define` creates text substitutions, including macros with arguments.
- Use parentheses carefully in macros.
- Conditional compilation lets you include or skip code based on macros.
- `#ifndef`, `#define`, `#endif` form header guards.

The preprocessor is a powerful text tool, but with that power comes the need for careful use.