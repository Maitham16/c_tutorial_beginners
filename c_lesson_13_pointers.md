# Lesson 13: Pointers

## What you will learn

- What a pointer is in plain language.
- How memory addresses work.
- How to declare, assign, and use pointers.
- What `NULL` means and why it is useful.

---

## Why pointers matter

A pointer is one of the most powerful and most feared ideas in C. Do not worry. It is simpler than it looks.

A pointer is just a variable that stores a memory address. That address tells the computer where another variable lives.

Think of memory like a city. Each variable lives in a house with a unique address. A pointer is a piece of paper with one of those addresses written on it.

---

## Variables live at addresses

Every variable in your program has a location in memory. The computer assigns it an address.

```c
#include <stdio.h>

int main() {
    int age = 25;

    printf("Value: %d\n", age);
    printf("Address: %p\n", &age);

    return 0;
}
```

Output:

```
Value: 25
Address: 0x7ffd8c4f2a4c
```

The `%p` specifier prints an address. The exact address will be different every time you run the program. The `&` operator means "the address of." So `&age` means "where `age` lives in memory."

---

## Declaring a pointer

To declare a pointer, you write the type it points to, followed by an asterisk, followed by the pointer name.

```c
int *pAge;
```

This says: `pAge` is a pointer that can hold the address of an `int`.

```c
#include <stdio.h>

int main() {
    int age = 25;
    int *pAge = &age;

    printf("Value of age: %d\n", age);
    printf("Address of age: %p\n", pAge);

    return 0;
}
```

Output:

```
Value of age: 25
Address of age: 0x7ffd8c4f2a4c
```

`pAge` now holds the address of `age`.

---

## Dereferencing a pointer

Dereferencing means following the address to get the value stored there. Use the asterisk in front of the pointer name.

```c
#include <stdio.h>

int main() {
    int age = 25;
    int *pAge = &age;

    printf("age: %d\n", age);
    printf("*pAge: %d\n", *pAge);

    *pAge = 30;

    printf("age after change: %d\n", age);

    return 0;
}
```

Output:

```
age: 25
*pAge: 25
age after change: 30
```

`*pAge = 30` means "go to the address stored in `pAge` and put 30 there." Since `pAge` points to `age`, changing `*pAge` also changes `age`.

---

## The two meanings of `*`

This is the part that confuses people, so read carefully.

- In a declaration, `int *p;` means `p` is a pointer.
- In an expression, `*p` means "the value at the address stored in `p`.

The same symbol does two related jobs. Context tells you which one is happening.

---

## NULL pointers

A pointer that does not point anywhere useful should be set to `NULL`.

```c
int *pNumber = NULL;
```

`NULL` is a special value that means "this pointer is not pointing to a valid address." Using a `NULL` pointer by mistake is still a bug, but it is easier to detect than using a random address.

---

## Why are pointers useful?

Pointers let you:
- Share data between functions without copying large values.
- Work with arrays and strings efficiently.
- Allocate memory while the program runs.
- Build complex data structures like linked lists and trees.

All of those will make more sense as you continue.

---

## Common beginner mistakes

- **Forgetting to initialize a pointer.** It will point to a random address.
- **Forgetting the `&` when assigning an address.** `pAge = age;` is wrong. Use `pAge = &age;`.
- **Forgetting the `*` when reading the value.** `printf("%d", pAge);` prints an address, not the value.
- **Using an uninitialized or dangling pointer.** This can crash the program.

---

## Mini exercises

1. Declare an `int` variable, a pointer to it, and print both the value and the address.
2. Use a pointer to change the value of a variable from 10 to 100.
3. Create two pointers that both point to the same variable. Change the value through one pointer and print through the other.

---

## Recap

- A pointer stores a memory address.
- `&` gives the address of a variable.
- `*` in a declaration declares a pointer.
- `*` in an expression follows the pointer to the value.
- `NULL` means the pointer points to nothing valid.

Pointers are the bridge between your variable names and the actual memory where data lives.