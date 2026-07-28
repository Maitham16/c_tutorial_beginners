# Lesson 8: Loops

## What you will learn

- How to repeat code with `for`, `while`, and `do while`.
- How to control loops with `break` and `continue`.
- How to avoid infinite loops.
- When to choose each kind of loop.

---

## Why loops exist

Computers are great at repetition. If you need to print numbers from 1 to 100, you do not want to write 100 `printf` statements. A **loop** lets you write the action once and tell the computer how many times to do it.

---

## The `for` loop

A `for` loop is best when you know how many times you want to repeat something.

```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 5; i++) {
        printf("%d\n", i);
    }

    return 0;
}
```

Output:

```
1
2
3
4
5
```

The `for` loop has three parts separated by semicolons:

1. `int i = 1` — run once before the loop starts.
2. `i <= 5` — check before every iteration. If true, run the body.
3. `i++` — run after every iteration.

You can read it as: "Start `i` at 1. While `i` is less than or equal to 5, print `i` and then add 1 to `i`."

---

## The `while` loop

A `while` loop is best when you do not know exactly how many times to repeat, but you know when to stop.

```c
#include <stdio.h>

int main() {
    int number = 1;

    while (number <= 5) {
        printf("%d\n", number);
        number++;
    }

    return 0;
}
```

Output:

```
1
2
3
4
5
```

The condition is checked before every iteration. If it starts false, the body never runs.

---

## The `do while` loop

A `do while` loop checks the condition after the body. This means the body always runs at least once.

```c
#include <stdio.h>

int main() {
    int number = 1;

    do {
        printf("%d\n", number);
        number++;
    } while (number <= 5);

    return 0;
}
```

Output:

```
1
2
3
4
5
```

Use `do while` when you want the action to happen before the first check.

---

## `break` and `continue`

- `break` exits the loop immediately.
- `continue` skips the rest of the current iteration and moves to the next one.

```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 10; i++) {
        if (i == 5) {
            continue;  // skip 5
        }
        if (i == 8) {
            break;       // stop at 8
        }
        printf("%d\n", i);
    }

    return 0;
}
```

Output:

```
1
2
3
4
6
7
```

The number 5 is skipped because of `continue`. The loop stops at 8 because of `break`.

---

## Infinite loops

An infinite loop never stops because its condition is always true. Sometimes this is intentional, like in a server waiting for requests. Often it is a mistake.

```c
#include <stdio.h>

int main() {
    while (1) {
        printf("This will run forever.\n");
    }

    return 0;
}
```

If you accidentally write an infinite loop, your program will hang. In an online compiler, you can stop it with the Stop button. On your computer, press Ctrl+C in the terminal.

To avoid accidental infinite loops, make sure something inside the loop changes the condition.

---

## Choosing a loop

| Situation                              | Best choice |
|----------------------------------------|-------------|
| You know the number of iterations      | `for`       |
| You wait for a condition to become false | `while`  |
| The body must run at least once        | `do while`  |

---

## Common beginner mistakes

- **Forgetting to update the loop variable.** This causes an infinite loop.
- **Using `=` instead of `==` in the loop condition.**
- **Off-by-one errors.** Think carefully whether to use `<` or `<=`. Counting from 0 vs 1 matters.
- **Modifying the loop variable inside the body in a confusing way.** Keep the loop logic simple.

---

## Mini exercises

1. Print the multiplication table for 7, from 1 to 10.
2. Ask the user to enter numbers until they type 0, then print the sum.
3. Print all even numbers from 2 to 20.

---

## Recap

- `for` loops are great for counted repetition.
- `while` loops repeat while a condition is true.
- `do while` loops run the body at least once.
- `break` exits a loop; `continue` skips to the next iteration.
- Always make sure the loop condition can become false.

Loops let your programs do a lot of work with very little code.