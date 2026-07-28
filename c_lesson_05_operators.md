# Lesson 5: Operators

## What you will learn

- How to do math in C using arithmetic operators.
- How to assign values with assignment operators.
- How to compare values and combine conditions.
- The order in which operations happen.

---

## Arithmetic operators

C can do math using these symbols:

| Operator | Meaning        | Example   | Result |
|----------|----------------|-----------|--------|
| `+`      | Addition       | `5 + 3`   | 8      |
| `-`      | Subtraction    | `5 - 3`   | 2      |
| `*`      | Multiplication | `5 * 3`   | 15     |
| `/`      | Division       | `10 / 2`  | 5      |
| `%`      | Remainder      | `10 % 3`  | 1      |

Example:

```c
#include <stdio.h>

int main() {
    int a = 17;
    int b = 5;

    printf("Sum: %d\n", a + b);
    printf("Difference: %d\n", a - b);
    printf("Product: %d\n", a * b);
    printf("Quotient: %d\n", a / b);
    printf("Remainder: %d\n", a % b);

    return 0;
}
```

Output:

```
Sum: 22
Difference: 12
Product: 85
Quotient: 3
Remainder: 2
```

Notice that `17 / 5` gives `3`, not `3.4`. When both numbers are `int`, C does **integer division** and drops the decimal part. If you want decimals, at least one number must be a `float` or `double`.

---

## Assignment operators

You already know the basic assignment operator `=`.

```c
int x = 10;
```

C also has shortcut operators for updating a variable:

| Operator | Example     | Same as        |
|----------|-------------|----------------|
| `+=`     | `x += 5`    | `x = x + 5`    |
| `-=`     | `x -= 5`    | `x = x - 5`    |
| `*=`     | `x *= 5`    | `x = x * 5`    |
| `/=`     | `x /= 5`    | `x = x / 5`    |
| `%=`     | `x %= 5`    | `x = x % 5`    |

Example:

```c
#include <stdio.h>

int main() {
    int score = 50;

    score += 10;  // score is now 60
    score *= 2;   // score is now 120

    printf("Final score: %d\n", score);
    return 0;
}
```

Output:

```
Final score: 120
```

---

## Increment and decrement

Two special operators are very common in C:

```c
x++;  // increase x by 1
x--;  // decrease x by 1
```

They can be placed before or after the variable, and the difference matters in larger expressions. For now, use them on their own line and the behavior is simple: the value changes by one.

---

## Comparison operators

Comparison operators check a relationship and return either true or false. In C, true is represented by `1` and false by `0`.

| Operator | Meaning                  | Example  | Result |
|----------|--------------------------|----------|--------|
| `==`     | Equal to                 | `5 == 5` | true   |
| `!=`     | Not equal to             | `5 != 3` | true   |
| `<`      | Less than                | `3 < 5`  | true   |
| `>`      | Greater than             | `5 > 3`  | true   |
| `<=`     | Less than or equal to    | `5 <= 5` | true   |
| `>=`     | Greater than or equal to | `4 >= 7` | false  |

Example:

```c
#include <stdio.h>

int main() {
    int a = 5;
    int b = 10;

    printf("Is a equal to b? %d\n", a == b);
    printf("Is a less than b? %d\n", a < b);

    return 0;
}
```

Output:

```
Is a equal to b? 0
Is a less than b? 1
```

---

## Logical operators

Logical operators combine true and false values.

| Operator | Meaning    | Example             | Result |
|----------|------------|---------------------|--------|
| `&&`    | AND        | `1 && 0`           | false  |
| `||`     | OR         | `1 || 0`            | true   |
| `!`      | NOT        | `!1`                | false  |

Example:

```c
#include <stdio.h>

int main() {
    int age = 25;
    int hasLicense = 1;

    printf("Can rent a car? %d\n", age >= 21 && hasLicense);

    return 0;
}
```

Output:

```
Can rent a car? 1
```

---

## Operator precedence

When multiple operators appear in one expression, C follows rules about which to do first. Parentheses let you control this yourself.

```c
int result = 5 + 3 * 2;      // result is 11, because * happens before +
int better = (5 + 3) * 2;    // result is 16
```

A good habit is to add parentheses whenever the order is not obvious. Code is read more often than it is written.

---

## Common beginner mistakes

- **Confusing `=` with `==`.** `=` assigns a value. `==` compares two values. This is one of the most common bugs in C.
- **Integer division surprises.** `7 / 2` is `3`, not `3.5`, when both are `int`.
- **Dividing by zero.** This crashes your program. Always check the denominator if it could be zero.
- **Forgetting parentheses.** When in doubt, use parentheses to make order clear.

---

## Mini exercises

1. Write a program that converts Celsius to Fahrenheit using the formula `F = C * 9 / 5 + 32`.
2. Create two `int` variables and print the remainder of their division.
3. Write an expression using `&&` and `||` to check if someone can enter a museum: age under 18 OR age over 65 gets free entry.

---

## Recap

- Arithmetic operators do math: `+`, `-`, `*`, `/`, `%`.
- Assignment shortcuts like `+=` and `++` save typing.
- Comparisons return `1` for true and `0` for false.
- Logical operators combine conditions: `&&`, `||`, `!`.
- Parentheses make operation order clear.
- Be careful not to confuse `=` with `==`.

Operators turn your variables into useful calculations and decisions.