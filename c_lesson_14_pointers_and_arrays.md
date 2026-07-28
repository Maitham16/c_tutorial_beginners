# Lesson 14: Pointers and Arrays

## What you will learn

- How arrays and pointers are related.
- What pointer arithmetic is.
- How to pass arrays to functions.
- Why arrays do not remember their own size.

---

## Arrays are pointers in disguise

In C, the name of an array is almost the same as a pointer to its first element. If you have an array `numbers`, then `numbers` is the address of `numbers[0]`.

```c
#include <stdio.h>

int main() {
    int numbers[3] = {10, 20, 30};

    printf("First element: %d\n", numbers[0]);
    printf("First element using pointer: %d\n", *numbers);

    return 0;
}
```

Output:

```
First element: 10
First element using pointer: 10
```

`numbers[0]` and `*numbers` give the same value because both start at the same address.

---

## Accessing other elements with pointers

Since `numbers` points to the first element, `numbers + 1` points to the second element, `numbers + 2` points to the third, and so on.

```c
#include <stdio.h>

int main() {
    int numbers[3] = {10, 20, 30};

    printf("Element 0: %d\n", *(numbers + 0));
    printf("Element 1: %d\n", *(numbers + 1));
    printf("Element 2: %d\n", *(numbers + 2));

    return 0;
}
```

Output:

```
Element 0: 10
Element 1: 20
Element 2: 30
```

Notice that `numbers + 1` does not add one byte. It adds one `int`, because the compiler knows the type. This is called **pointer arithmetic**.

---

## Array indexing is pointer arithmetic

When you write `numbers[i]`, the compiler treats it as `*(numbers + i)`. This is why arrays start at index 0.

```c
numbers[0] == *(numbers + 0)
numbers[1] == *(numbers + 1)
```

Both styles work, but `numbers[i]` is usually easier to read.

---

## Passing arrays to functions

When you pass an array to a function, you are really passing a pointer to its first element. The function does not receive a copy of the whole array. It receives the address where the array begins.

Because of this, arrays do not know their own size. You usually pass the size as a second argument.

```c
#include <stdio.h>

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int values[5] = {3, 7, 2, 9, 4};

    printArray(values, 5);

    return 0;
}
```

Output:

```
3 7 2 9 4
```

You can also write the function parameter as a pointer:

```c
void printArray(int *arr, int size)
```

Both versions mean the same thing.

---

## Modifying arrays inside functions

Because the function receives the address of the array, changes made inside the function affect the original array.

```c
#include <stdio.h>

void doubleValues(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        arr[i] = arr[i] * 2;
    }
}

int main() {
    int values[3] = {1, 2, 3};

    doubleValues(values, 3);

    for (int i = 0; i < 3; i++) {
        printf("%d ", values[i]);
    }
    printf("\n");

    return 0;
}
```

Output:

```
2 4 6
```

The original array changed because the function worked on the real memory, not a copy.

---

## Common beginner mistakes

- **Expecting the array to know its size inside a function.** The function only receives a pointer. Always pass the size.
- **Confusing bytes with elements in pointer arithmetic.** `arr + 1` moves by one element, not one byte.
- **Trying to assign one array to another.** Arrays cannot be copied with `=`. Use a loop or `memcpy`.

---

## Mini exercises

1. Write a function that sums all elements of an integer array.
2. Write a function that reverses an array in place.
3. Use pointer arithmetic to print every element of an array without using square brackets.

---

## Recap

- An array name is a pointer to its first element.
- `arr[i]` is the same as `*(arr + i)`.
- Pointer arithmetic moves by the size of the type.
- When you pass an array to a function, you pass a pointer.
- Functions that receive arrays can modify the original data.
- Always pass the array size along with the array.

Once you see arrays as pointers, many ideas in C start to click together.