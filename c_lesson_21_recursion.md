# Lesson 21: Recursion

## What you will learn

- What recursion is and how it works.
- The importance of a base case.
- How to write recursive functions.
- When recursion helps and when it can hurt.

---

## What is recursion?

Recursion is when a function calls itself. It sounds strange at first, but it is a natural way to solve problems that can be broken into smaller versions of themselves.

Think of a set of Russian nesting dolls. Each doll contains a smaller version of itself. Recursion works the same way: a big problem is solved by solving a smaller version of the same problem, then a smaller one, until you reach the simplest case.

---

## The two parts every recursive function needs

Every recursive function needs:

1. A **base case** — the simplest version of the problem, which stops the recursion.
2. A **recursive case** — the function calls itself with a smaller or simpler input.

Without a base case, the function calls itself forever, causing a **stack overflow**.

---

## Example: factorial

The factorial of a number n is the product of all positive integers up to n.

```
5! = 5 * 4 * 3 * 2 * 1 = 120
```

You can also think of it as:

```
5! = 5 * 4!
4! = 4 * 3!
...
1! = 1
```

This is perfect for recursion.

```c
#include <stdio.h>

int factorial(int n) {
    if (n <= 1) {
        return 1;  // base case
    }

    return n * factorial(n - 1);  // recursive case
}

int main() {
    printf("5! = %d\n", factorial(5));

    return 0;
}
```

Output:

```
5! = 120
```

Each call waits for the result of the smaller call. Eventually, `factorial(1)` returns `1`, and the results bubble back up.

---

## Example: Fibonacci sequence

The Fibonacci sequence starts with 0 and 1, and each following number is the sum of the two before it.

```
0, 1, 1, 2, 3, 5, 8, 13, 21, ...
```

```c
#include <stdio.h>

int fibonacci(int n) {
    if (n == 0) {
        return 0;
    }
    if (n == 1) {
        return 1;
    }

    return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    for (int i = 0; i < 10; i++) {
        printf("%d ", fibonacci(i));
    }
    printf("\n");

    return 0;
}
```

Output:

```
0 1 1 2 3 5 8 13 21 34
```

This version is simple but slow. It recalculates the same values many times.

---

## Recursion vs loops

Many problems can be solved with either recursion or loops. Recursion is often clearer for problems that have a natural recursive structure, like tree traversal or divide-and-conquer algorithms. Loops are usually more efficient for simple repetition.

Use recursion when it makes the solution easier to understand. Use a loop when performance matters and the problem is naturally repetitive.

---

## The danger of missing the base case

If a recursive function never reaches a base case, it keeps calling itself until the stack runs out of memory. This is called a **stack overflow**.

```c
int bad(int n) {
    return bad(n - 1);  // never stops
}
```

Always make sure the input moves closer to the base case with every call.

---

## Common beginner mistakes

- **Forgetting the base case.** The function will run forever or crash.
- **Not moving toward the base case.** Each recursive call should reduce the problem.
- **Using recursion when a simple loop would be clearer.** Recursion is not always better.
- **Not understanding the call stack.** Each call waits, using memory, until the base case returns.

---

## Mini exercises

1. Write a recursive function that sums all numbers from 1 to n.
2. Write a recursive function that prints a string in reverse.
3. Try calculating `fibonacci(40)` with the simple version. Notice how long it takes. Why is it slow?

---

## Recap

- Recursion is a function calling itself.
- Every recursive function needs a base case and a recursive case.
- The base case stops the recursion.
- Recursion is elegant for naturally recursive problems.
- Missing the base case causes a stack overflow.

Recursion teaches you to think about problems as smaller versions of themselves.