# Lesson 6: Reading Input and Printing Output

## What you will learn

- How to use `printf` to display formatted text.
- How to use `scanf` to read input from the user.
- How to read numbers and characters safely.
- Why the ampersand in `scanf` matters.

---

## Printing with `printf`

`printf` is the most common way to send text to the screen. The "f" stands for formatted, which means you can control how values appear.

```c
#include <stdio.h>

int main() {
    int age = 20;
    float height = 1.68;

    printf("I am %d years old.\n", age);
    printf("I am %.2f meters tall.\n", height);

    return 0;
}
```

Output:

```
I am 20 years old.
I am 1.68 meters tall.
```

The `%.2f` means "print a float with two digits after the decimal point." You can change the number to show more or fewer decimals.

---

## Reading with `scanf`

`scanf` reads what the user types. It uses the same format specifiers as `printf`.

```c
#include <stdio.h>

int main() {
    int age;

    printf("How old are you? ");
    scanf("%d", &age);

    printf("You are %d years old.\n", age);

    return 0;
}
```

Sample run:

```
How old are you? 22
You are 22 years old.
```

The `&` before `age` is very important. It gives `scanf` the memory address of the variable so it can store the typed value there. We will understand addresses fully in the pointers lesson, but for now remember this rule:

> When using `scanf` with numbers or characters, put `&` before the variable name.

---

## Reading multiple values

You can read more than one value in a single `scanf`.

```c
#include <stdio.h>

int main() {
    int length;
    int width;

    printf("Enter length and width: ");
    scanf("%d %d", &length, &width);

    printf("Area: %d\n", length * width);

    return 0;
}
```

Sample run:

```
Enter length and width: 8 5
Area: 40
```

The user can separate the two numbers with a space, a tab, or a newline.

---

## Reading a character

To read a single character, use `%c`.

```c
#include <stdio.h>

int main() {
    char grade;

    printf("Enter your grade: ");
    scanf(" %c", &grade);

    printf("Your grade is %c.\n", grade);

    return 0;
}
```

Notice the space before `%c`. That space tells `scanf` to skip any leftover whitespace, like the newline from pressing Enter. Without it, `scanf` might read the newline instead of the letter you typed.

---

## Reading a decimal number

Use `%f` for `float` and `%lf` for `double`.

```c
#include <stdio.h>

int main() {
    double price;

    printf("Enter the price: ");
    scanf("%lf", &price);

    printf("Price: %.2f\n", price);

    return 0;
}
```

Sample run:

```
Enter the price: 19.99
Price: 19.99
```

---

## Common beginner mistakes

- **Forgetting `&` in `scanf`.** Without it, the program may crash or behave strangely.
- **Using `%f` for `double` in `scanf`.** Use `%lf` for `double` when reading.
- **Reading a character right after a number without a space.** The leftover newline will be read as your character.
- **Typing text when a number is expected.** `scanf` will fail and leave the variable unchanged.

---

## Mini exercises

1. Ask the user for their name length? Instead read their first initial as a `char` and print it.
2. Read two `float` values and print their average with two decimal places.
3. Read a temperature in Celsius and convert it to Fahrenheit.

---

## Recap

- `printf` prints formatted text to the screen.
- `scanf` reads input from the user.
- Use `&` before variables in `scanf` for numbers and characters.
- `%d` for `int`, `%f` for `float`, `%lf` for `double`, `%c` for `char`.
- Add a space before `%c` if you want to skip leftover newlines.

Now your programs can talk to the person running them.