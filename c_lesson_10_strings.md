# Lesson 10: Strings

## What you will learn

- How C stores text as arrays of characters.
- What the null terminator is and why it matters.
- How to create, print, and copy strings.
- How to use a few helpers from `string.h`.

---

## What is a string?

In C, a string is not its own type. It is an array of `char` values that ends with a special character called the **null terminator**, written as `\0`. It tells functions where the string ends.

Think of a string as a line of letters with an invisible stop sign at the end.

---

## Creating a string

The easiest way is to use double quotes:

```c
char name[] = "Alice";
```

This creates an array with six characters, not five:

| Index | 0   | 1   | 2   | 3   | 4   | 5   |
|-------|-----|-----|-----|-----|-----|-----|
| Char  | 'A' | 'l' | 'i' | 'c' | 'e' | '\0' |

The compiler adds the null terminator for you. This is why strings declared this way are safe to print and pass to functions.

---

## Printing a string

Use `%s` with `printf`:

```c
#include <stdio.h>

int main() {
    char name[] = "Alice";

    printf("Hello, %s!\n", name);

    return 0;
}
```

Output:

```
Hello, Alice!
```

---

## Reading a string with `scanf`

Use `%s` to read a single word. Be careful: `scanf` does not know how large your array is, so it can write past the end if the user types too much.

```c
#include <stdio.h>

int main() {
    char name[20];

    printf("Enter your name: ");
    scanf("%s", name);

    printf("Hello, %s!\n", name);

    return 0;
}
```

Notice there is no `&` before `name`. That is because the name of an array is already treated as the address where it begins. We will explain this fully in the pointers lessons.

For safety, you can tell `scanf` the maximum length to read:

```c
scanf("%19s", name);  // leaves room for the null terminator
```

---

## The `string.h` helpers

C gives you a library called `string.h` with useful string functions.

### `strlen` — string length

```c
#include <stdio.h>
#include <string.h>

int main() {
    char word[] = "hello";

    printf("Length: %lu\n", strlen(word));

    return 0;
}
```

Output:

```
Length: 5
```

`strlen` counts characters but not the null terminator. The `%lu` is the format specifier for an unsigned long integer, which is what `strlen` returns.

### `strcpy` — copy a string

```c
#include <stdio.h>
#include <string.h>

int main() {
    char source[] = "copy me";
    char destination[20];

    strcpy(destination, source);

    printf("Copied: %s\n", destination);

    return 0;
}
```

Output:

```
Copied: copy me
```

`strcpy` copies every character, including the null terminator. Make sure the destination is big enough.

### `strcmp` — compare strings

```c
#include <stdio.h>
#include <string.h>

int main() {
    char a[] = "apple";
    char b[] = "banana";

    if (strcmp(a, b) == 0) {
        printf("The strings are equal.\n");
    } else {
        printf("The strings are different.\n");
    }

    return 0;
}
```

Output:

```
The strings are different.
```

`strcmp` returns `0` if the strings are equal, a negative number if the first is smaller, and a positive number if the first is larger.

---

## Common beginner mistakes

- **Using `==` to compare strings.** This compares memory addresses, not content. Always use `strcmp`.
- **Forgetting space for the null terminator.** A string with 5 visible characters needs at least 6 bytes.
- **Writing past the end of the array.** This corrupts memory and can crash the program.
- **Trying to assign one string to another after declaration.** You cannot write `a = b;` for arrays. Use `strcpy`.

---

## Mini exercises

1. Ask the user for their first name and last name, then print them together.
2. Create two strings and print whether they are equal or not.
3. Count how many characters are in your favorite word using `strlen`.

---

## Recap

- A string is an array of `char` values ending with `\0`.
- Use `%s` to print strings with `printf`.
- Use `string.h` for helpers like `strlen`, `strcpy`, and `strcmp`.
- Never compare strings with `==`.
- Always leave room for the null terminator.

Strings are everywhere in programs. Understanding how C handles them gives you a deeper view of how memory works.