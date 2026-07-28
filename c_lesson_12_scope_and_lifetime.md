# Lesson 12: Scope and Lifetime

## What you will learn

- What scope means and how it limits where variables can be used.
- The difference between local and global variables.
- What `static` variables are and when to use them.
- Why minimizing scope makes programs safer.

---

## What is scope?

Scope is the part of the program where a variable is visible and usable. If you try to use a variable outside its scope, the compiler will complain because it does not know what you are talking about.

Think of scope like a room. A variable declared inside a room only exists while you are in that room.

---

## Local variables

A variable declared inside a function is called a **local variable**. It only exists inside that function.

```c
#include <stdio.h>

void example() {
    int number = 10;
    printf("Inside example: %d\n", number);
}

int main() {
    example();
    // printf("%d\n", number);  // This would cause an error

    return 0;
}
```

Output:

```
Inside example: 10
```

`number` lives inside `example`. `main` cannot see it. This is good. It means one function cannot accidentally mess with another function's variables.

---

## Global variables

A variable declared outside every function is called a **global variable**. It can be used by any function in the file.

```c
#include <stdio.h>

int counter = 0;  // global variable

void increase() {
    counter++;
    printf("Counter: %d\n", counter);
}

int main() {
    increase();
    increase();
    increase();

    return 0;
}
```

Output:

```
Counter: 1
Counter: 2
Counter: 3
```

Global variables are convenient, but they can make programs harder to understand. When many functions can change the same variable, bugs become harder to find. As a beginner, use local variables whenever possible.

---

## Block scope

A variable declared inside a block, which is anything inside `{ }`, only exists in that block.

```c
#include <stdio.h>

int main() {
    int outer = 5;

    if (outer > 0) {
        int inner = 10;
        printf("Inside block: %d\n", inner);
    }

    // printf("%d\n", inner);  // Error: inner does not exist here

    return 0;
}
```

Output:

```
Inside block: 10
```

A block can be the body of a function, an `if`, a loop, or even a standalone pair of braces.

---

## Variable lifetime

Lifetime means how long a variable exists in memory.

- A local variable is created when its function starts and destroyed when the function ends.
- A global variable exists for the entire run of the program.

This matters because a local variable disappears after the function returns. You should not try to return the address of a local variable. We will cover why when we study pointers.

---

## The `static` keyword

A local variable declared with `static` keeps its value between function calls.

```c
#include <stdio.h>

void countCalls() {
    static int calls = 0;
    calls++;
    printf("This function has been called %d time(s).\n", calls);
}

int main() {
    countCalls();
    countCalls();
    countCalls();

    return 0;
}
```

Output:

```
This function has been called 1 time(s).
This function has been called 2 time(s).
This function has been called 3 time(s).
```

The line `static int calls = 0;` only runs once. After that, `calls` remembers its value.

---

## Common beginner mistakes

- **Trying to use a local variable outside its function.** The compiler will say the variable is undeclared.
- **Overusing global variables.** They make it harder to track where changes happen.
- **Thinking `static` makes a variable constant.** It does not. It only changes lifetime, not whether the value can change.

---

## Mini exercises

1. Create a local variable inside a function and try to print it from `main`. What error do you get?
2. Write a function with a `static` local variable that keeps a running total.
3. Refactor a program that uses a global variable so the data is passed as parameters instead.

---

## Recap

- Scope determines where a variable can be used.
- Local variables live inside functions and blocks.
- Global variables live outside functions and are visible everywhere.
- Local variables are created and destroyed with their function.
- `static` local variables keep their value between function calls.
- Keep variables as local as possible to avoid confusion.

Understanding scope helps you keep your code organized and bug-free.