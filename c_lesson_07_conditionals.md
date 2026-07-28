# Lesson 7: Making Decisions with Conditionals

## What you will learn

- How to make your program choose between different paths.
- How to use `if`, `else if`, and `else`.
- How `switch` handles many specific choices.
- The difference between `==` and `=`.

---

## Why conditionals matter

So far, every program has run from top to bottom exactly the same way every time. Real programs need to react. They need to ask questions and do different things based on the answers.

Conditionals let your code make decisions.

---

## The `if` statement

The simplest conditional checks one condition. If the condition is true, the code inside the braces runs. If not, it is skipped.

```c
#include <stdio.h>

int main() {
    int age;

    printf("How old are you? ");
    scanf("%d", &age);

    if (age >= 18) {
        printf("You are an adult.\n");
    }

    printf("Program finished.\n");
    return 0;
}
```

If the user types `20`, the program prints:

```
You are an adult.
Program finished.
```

If the user types `15`, it only prints:

```
Program finished.
```

---

## Adding `else`

Use `else` to run code when the condition is false.

```c
#include <stdio.h>

int main() {
    int temperature;

    printf("What is the temperature? ");
    scanf("%d", &temperature);

    if (temperature >= 25) {
        printf("It is warm.\n");
    } else {
        printf("It is cool.\n");
    }

    return 0;
}
```

Only one branch runs. It is either warm or cool, never both.

---

## Adding `else if`

When you have more than two choices, use `else if`.

```c
#include <stdio.h>

int main() {
    int score;

    printf("Enter your score: ");
    scanf("%d", &score);

    if (score >= 90) {
        printf("Grade: A\n");
    } else if (score >= 80) {
        printf("Grade: B\n");
    } else if (score >= 70) {
        printf("Grade: C\n");
    } else if (score >= 60) {
        printf("Grade: D\n");
    } else {
        printf("Grade: F\n");
    }

    return 0;
}
```

The conditions are checked from top to bottom. As soon as one is true, its block runs and the rest are skipped.

---

## The `switch` statement

`switch` is useful when you want to compare one variable against many exact values.

```c
#include <stdio.h>

int main() {
    int day;

    printf("Enter a day number (1-7): ");
    scanf("%d", &day);

    switch (day) {
        case 1:
            printf("Monday\n");
            break;
        case 2:
            printf("Tuesday\n");
            break;
        case 3:
            printf("Wednesday\n");
            break;
        case 4:
            printf("Thursday\n");
            break;
        case 5:
            printf("Friday\n");
            break;
        case 6:
            printf("Saturday\n");
            break;
        case 7:
            printf("Sunday\n");
            break;
        default:
            printf("Invalid day\n");
    }

    return 0;
}
```

The `break` keyword stops the `switch` from falling through to the next case. If you forget it, multiple cases can run.

`default` runs when none of the cases match, similar to `else`.

---

## The danger of `=` vs `==`

This is the most common conditional mistake in C.

```c
if (x = 5) {
```

This assigns `5` to `x` and then treats the result as true. It does not check whether `x` equals `5`. The correct version is:

```c
if (x == 5) {
```

A helpful habit is to put the constant on the left:

```c
if (5 == x) {
```

If you accidentally type `if (5 = x)`, the compiler will catch it because you cannot assign a value to a number.

---

## Common beginner mistakes

- **Using `=` instead of `==` in comparisons.**
- **Forgetting braces for multi-line blocks.** Without braces, only the first line after `if` is included.
- **Forgetting `break` in `switch`, causing fall-through behavior unintentionally.**
- **Checking ranges the wrong way.** `if (60 <= score <= 100)` does not work in C the way you might expect. Use `if (score >= 60 && score <= 100)`.

---

## Mini exercises

1. Ask the user for a number and print whether it is positive, negative, or zero.
2. Read a letter grade as a character and print a motivational message for each grade.
3. Ask for the current hour and print "Good morning", "Good afternoon", or "Good evening".

---

## Recap

- `if` runs code when a condition is true.
- `else` runs code when the condition is false.
- `else if` lets you check multiple conditions in order.
- `switch` checks one value against many exact cases.
- Use `==` to compare, not `=`.
- `break` stops a `switch` case from falling through.

Conditionals give your programs the power to react.