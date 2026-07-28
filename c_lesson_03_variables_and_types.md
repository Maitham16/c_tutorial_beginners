# Lesson 3: Variables and Data Types

## What you will learn

- What a variable is and how it works in memory.
- The four most common data types: `int`, `float`, `double`, and `char`.
- How to declare and use variables.
- Rules for naming variables and why names matter.

---

## What is a variable?

A variable is a named place in memory where you can store a value. Think of it like a labeled box. The label is the name you use in your code. The box holds the value.

For example, if you want to remember someone's age, you can create a box called `age` and put the number 25 inside it. Later in your program, you can open the box, read the number, or replace it with a new one.

---

## Declaring a variable

Before you use a variable, you must declare it. Declaring means telling the compiler two things: what type of value the variable will hold, and what name you want to give it.

```c
int age;
```

This says, "Create a box that can hold an integer and name it `age`."

You can also give it a value right away:

```c
int age = 25;
```

This is called **initialization**.

---

## The main data types

### `int` — whole numbers

Use `int` for numbers without decimals. Examples: 0, -3, 42, 1000.

```c
int score = 95;
int temperature = -5;
```

### `float` — numbers with decimals

Use `float` for numbers that may have a decimal part. Examples: 3.14, -0.5, 9.81.

```c
float price = 19.99;
float gravity = 9.81;
```

### `double` — more precise decimals

A `double` is like a `float` but can store more digits. Use it when precision matters, such as scientific calculations.

```c
double pi = 3.1415926535;
```

### `char` — single characters

Use `char` for one letter, digit, or symbol. A `char` value goes inside single quotes.

```c
char grade = 'A';
char symbol = '$';
```

---

## Printing variables

To print a variable, you use a **format specifier** inside `printf`.

| Type    | Specifier |
|---------|-----------|
| int     | `%d`      |
| float   | `%f`      |
| double  | `%lf`     |
| char    | `%c`      |

Example:

```c
#include <stdio.h>

int main() {
    int age = 25;
    float height = 1.75;
    char grade = 'A';

    printf("Age: %d\n", age);
    printf("Height: %f meters\n", height);
    printf("Grade: %c\n", grade);

    return 0;
}
```

Output:

```
Age: 25
Height: 1.750000 meters
Grade: A
```

The value after the comma replaces the specifier in the text.

---

## Naming rules

Variable names must follow these rules:

- They can contain letters, digits, and underscores.
- They must start with a letter or underscore, not a digit.
- They cannot be C keywords like `int`, `return`, `if`, or `while`.
- C is case-sensitive, so `Age` and `age` are different variables.

Good names:

```c
int studentCount;
float totalPrice;
char firstInitial;
```

Bad names:

```c
int 2ndPlace;     // starts with a digit
float total$;      // $ is not allowed
int float;         // keyword not allowed
```

---

## Changing a variable

Once a variable exists, you can change its value with the assignment operator `=`.

```c
#include <stdio.h>

int main() {
    int score = 80;
    printf("Before: %d\n", score);

    score = 95;
    printf("After: %d\n", score);

    return 0;
}
```

Output:

```
Before: 80
After: 95
```

Notice that the second line does not say `int score` again. The variable already exists, so you only write the name.

---

## Common beginner mistakes

- **Using a variable before declaring it.** The compiler needs to know the type first.
- **Forgetting the format specifier.** `printf(score);` does not work.
- **Mismatching type and specifier.** Using `%d` to print a `float` gives strange results.
- **Confusing `=` and `==`.** `=` assigns a value. `==` checks equality. We will see `==` in the conditionals lesson.

---

## Mini exercises

1. Declare three variables: your birth year, your height in meters, and your first initial. Print all three.
2. Create an `int` variable called `cookies` set to 10. Print it, then set it to 7, then print it again.
3. What happens if you try to store a decimal number inside an `int`? Try it and observe the output.

---

## Recap

- A variable is a named box for storing data.
- You declare a variable with a type and a name.
- `int` holds whole numbers, `float` and `double` hold decimals, `char` holds one character.
- `printf` uses `%d`, `%f`, `%lf`, and `%c` to print different types.
- Names must start with a letter or underscore and cannot be keywords.

Variables are the foundation of almost every program you will write.