# Lesson 15: Strings and Pointers

## What you will learn

- How string literals are stored in memory.
- The difference between `char name[]` and `char *name`.
- Why modifying a string literal is dangerous.
- How to pass strings to functions safely.

---

## String literals

When you write a string inside double quotes, the compiler stores it somewhere in memory and gives you its address.

```c
char *message = "Hello";
```

Here, `message` is a pointer. It points to the first character of the string `"Hello"`, which the compiler has placed in memory. The string still ends with a null terminator.

```c
#include <stdio.h>

int main() {
    char *message = "Hello";

    printf("%s\n", message);
    printf("First letter: %c\n", message[0]);

    return 0;
}
```

Output:

```
Hello
First letter: H
```

You can use array-style indexing on a pointer because arrays and pointers are closely related.

---

## `char name[]` vs `char *name`

These two declarations look similar but behave differently.

### `char name[] = "Hello"`

This creates an array in memory and copies the string into it. You are allowed to change the contents.

```c
#include <stdio.h>

int main() {
    char name[] = "Hello";

    name[0] = 'J';
    printf("%s\n", name);

    return 0;
}
```

Output:

```
Jello
```

### `char *name = "Hello"`

This creates a pointer that points to a string literal. A string literal is usually stored in read-only memory. Trying to change it can crash your program.

```c
#include <stdio.h>

int main() {
    char *name = "Hello";

    // name[0] = 'J';  // DANGEROUS: may crash

    printf("%s\n", name);

    return 0;
}
```

The safe rule is:

> Use `char name[]` if you want to change the string. Use `char *name` only if you want to read it.

---

## Passing strings to functions

When you pass a string to a function, you are passing a pointer to the first character. The function does not need the size because the null terminator marks the end.

```c
#include <stdio.h>

void printLength(char *text) {
    int length = 0;
    while (text[length] != '\0') {
        length++;
    }
    printf("Length: %d\n", length);
}

int main() {
    char word[] = "programming";

    printLength(word);

    return 0;
}
```

Output:

```
Length: 11
```

The function walks through the string one character at a time until it finds the null terminator.

---

## Returning strings from functions

You cannot safely return a pointer to a local array from a function. The local array is destroyed when the function ends, so the pointer would point to invalid memory.

If you need to return a string, either:
- Pass in an array for the function to fill.
- Use dynamically allocated memory, which we will cover in the next lessons.

Example of passing an array in:

```c
#include <stdio.h>

void greet(char *buffer, int size) {
    // In real code, use snprintf to avoid overflow
    snprintf(buffer, size, "Hello, student!");
}

int main() {
    char message[50];

    greet(message, sizeof(message));
    printf("%s\n", message);

    return 0;
}
```

Output:

```
Hello, student!
```

---

## Common beginner mistakes

- **Modifying a string literal.** It may compile but can crash or behave unexpectedly.
- **Returning a pointer to a local array.** The memory no longer exists after the function returns.
- **Forgetting the null terminator.** Functions that work with strings rely on it.

---

## Mini exercises

1. Declare a string with `char word[]` and change the first letter to uppercase.
2. Write a function that counts how many vowels are in a string.
3. Explain to yourself why `char *word = "Hi"; word[0] = 'B';` is risky.

---

## Recap

- A string literal gives you a pointer to read-only memory.
- `char name[]` creates a modifiable copy of the string.
- `char *name` creates a pointer, often to a string you should not change.
- Functions receive strings as pointers and use the null terminator to find the end.
- Do not return pointers to local arrays.

Strings and pointers are deeply connected. Understanding both together makes C much less mysterious.