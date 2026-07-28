# Lesson 17: Memory Management

## What you will learn

- The difference between stack memory and heap memory.
- How to request memory while the program runs using `malloc`.
- How to release memory with `free`.
- What `calloc` and `realloc` do.
- Why memory leaks happen and how to avoid them.

---

## Stack vs heap

Your program uses two main areas of memory.

The **stack** is where local variables live. The system manages it automatically. When a function starts, space is reserved. When the function ends, the space is freed. You do not need to do anything.

The **heap** is a larger pool of memory that you manage yourself. It is useful when you do not know at compile time how much memory you will need, like when reading a list of unknown size from the user.

| Feature | Stack | Heap |
|---------|-------|------|
| Managed by | Compiler automatically | Programmer |
| Size | Small and fixed | Larger and flexible |
| Speed | Fast | Slower |
| Lifetime | Tied to function scope | Until you free it |

---

## Allocating memory with `malloc`

`malloc` stands for **memory allocate**. It asks the operating system for a block of memory of a certain size and returns the address where that block begins.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *numbers = malloc(5 * sizeof(int));

    if (numbers == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    for (int i = 0; i < 5; i++) {
        numbers[i] = i + 1;
    }

    for (int i = 0; i < 5; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");

    free(numbers);

    return 0;
}
```

Output:

```
1 2 3 4 5
```

`malloc(5 * sizeof(int))` asks for enough space for five integers. `sizeof(int)` returns the number of bytes one integer needs. Multiplying by five gives the total bytes needed.

Always check whether `malloc` returned `NULL`. If it did, the system could not give you memory.

---

## Releasing memory with `free`

Every block of memory you request with `malloc` must be returned with `free` when you are done. If you forget, you create a **memory leak**. The memory stays allocated but unreachable, and your program gradually uses more and more memory.

```c
free(numbers);
```

After freeing, do not use the pointer again unless you assign it a new valid address.

---

## Zeroed memory with `calloc`

`calloc` is similar to `malloc`, but it also sets every byte to zero before giving the memory to you. It takes two arguments: the number of elements and the size of each element.

```c
int *numbers = calloc(5, sizeof(int));
```

This is useful when you want all values to start at zero.

---

## Resizing memory with `realloc`

Sometimes you allocate memory and later realize you need more or less. `realloc` can resize an existing block.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *numbers = malloc(3 * sizeof(int));

    numbers[0] = 10;
    numbers[1] = 20;
    numbers[2] = 30;

    numbers = realloc(numbers, 5 * sizeof(int));

    numbers[3] = 40;
    numbers[4] = 50;

    for (int i = 0; i < 5; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");

    free(numbers);

    return 0;
}
```

Output:

```
10 20 30 40 50
```

`realloc` may move the data to a new location if the current block cannot grow. Always use the pointer it returns.

---

## Common beginner mistakes

- **Forgetting to check for `NULL` after `malloc`.**
- **Forgetting to call `free`.** This causes memory leaks.
- **Using memory after `free`.** This is undefined behavior and may crash.
- **Calling `free` twice on the same pointer.** This is a double free and is dangerous.
- **Using `malloc` without including `stdlib.h`.** The compiler may warn or produce incorrect code.

---

## Mini exercises

1. Allocate an array of 10 integers with `malloc`, fill it with multiples of 10, print it, then free it.
2. Use `calloc` to allocate space for 100 integers and confirm they all start at zero.
3. Use `realloc` to grow an array from 4 to 8 elements and fill the new slots.

---

## Recap

- The stack is automatic but limited.
- The heap is large but must be managed by you.
- `malloc` allocates memory; `free` returns it.
- `calloc` allocates and zeroes memory.
- `realloc` changes the size of an existing allocation.
- Always check for `NULL` and always free what you allocate.

Managing memory is a big responsibility, but it gives you precise control over what your program uses.