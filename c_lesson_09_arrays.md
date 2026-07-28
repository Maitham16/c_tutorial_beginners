# Lesson 9: Arrays

## What you will learn

- How to store many values under one name.
- How to declare, initialize, and access arrays.
- Why array indices start at 0.
- How to loop through an array.

---

## What is an array?

An array is a row of boxes that share the same name and store the same type of data. Think of it as a shelf with numbered compartments. You use the name of the shelf and the compartment number to find a value.

---

## Declaring an array

```c
int scores[5];
```

This creates space for five integers. The array is called `scores`. Each slot has a number, called an **index**, starting from 0.

| Index | 0 | 1 | 2 | 3 | 4 |
|-------|---|---|---|---|---|
| Value | ? | ? | ? | ? | ? |

At first, the values are uninitialized, which means they contain whatever was already in memory.

---

## Initializing an array

You can give values when you declare the array:

```c
int scores[5] = {85, 92, 78, 90, 88};
```

Now the array looks like this:

| Index | 0  | 1  | 2  | 3  | 4  |
|-------|----|----|----|----|----|
| Value | 85 | 92 | 78 | 90 | 88 |

You can also leave out the size if you provide values:

```c
int scores[] = {85, 92, 78, 90, 88};
```

The compiler counts five values for you.

---

## Accessing array elements

Use the index inside square brackets to read or change a value.

```c
#include <stdio.h>

int main() {
    int scores[5] = {85, 92, 78, 90, 88};

    printf("First score: %d\n", scores[0]);
    printf("Third score: %d\n", scores[2]);

    scores[2] = 95;
    printf("Updated third score: %d\n", scores[2]);

    return 0;
}
```

Output:

```
First score: 85
Third score: 78
Updated third score: 95
```

Notice that the third score is at index `2`, not `3`. This is the most important habit to build: **array indices start at 0**.

---

## Looping through an array

A `for` loop is the natural way to visit every element.

```c
#include <stdio.h>

int main() {
    int scores[5] = {85, 92, 78, 90, 88};
    int total = 0;

    for (int i = 0; i < 5; i++) {
        total = total + scores[i];
    }

    printf("Total: %d\n", total);
    printf("Average: %.2f\n", total / 5.0);

    return 0;
}
```

Output:

```
Total: 433
Average: 86.60
```

We use `i < 5` because the valid indices are 0, 1, 2, 3, and 4.

---

## Array bounds

C does not stop you from accessing an index outside the array. If you write `scores[10]`, the compiler will not complain, but you are reading or writing memory that does not belong to you. This can corrupt data or crash your program. Always make sure your index is within the valid range.

---

## Common beginner mistakes

- **Thinking the first element is at index 1.** It is at index 0.
- **Using `i <=` size.** If the array has 5 elements, the last valid index is 4. Use `< 5`, not `<= 5`.
- **Reading from an uninitialized element.** Values are not automatically zero unless you set them.
- **Going out of bounds.** C trusts you; it will not protect you from yourself.

---

## Mini exercises

1. Create an array of five temperatures and print the highest one.
2. Initialize an array with the numbers 1 to 10 and print them in reverse order.
3. Ask the user to enter five numbers, store them in an array, and print their sum.

---

## Recap

- An array stores multiple values of the same type under one name.
- Indices start at 0.
- Use square brackets to access or modify elements.
- `for` loops are perfect for processing arrays.
- Never access an index outside the array's bounds.

Arrays let you work with collections of data without creating dozens of variables.