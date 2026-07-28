# Lesson 2: How C Programs Work

## What you will learn

- What source code, machine code, and a compiler really do.
- Why C programs run from top to bottom.
- The difference between errors and warnings.
- How to read a compiler message without panicking.

---

## From human ideas to machine actions

When you write a C program, you are writing text that a human understands. The computer, however, only understands zeros and ones. Something has to translate your human-friendly code into instructions the processor can execute. That something is called a **compiler**.

Think of the compiler as a strict translator. You hand it a letter written in English, and it produces the same letter in the computer's native language. If your English is unclear or contains mistakes, the translator refuses to continue and tells you what is wrong.

---

## Source code and machine code

The file you write is called **source code**. It usually ends with `.c`, like `lesson.c`. When you click Run in an online compiler, or type `gcc lesson.c` on your computer, the compiler reads your source code and produces an executable program.

The executable is the translated version. It is not human-readable, but the computer can run it directly.

---

## Programs run top to bottom

Inside `main`, C executes your statements in order, from the first line to the last. It does not skip around unless you later tell it to with things like `if`, loops, or function calls.

Look at this program:

```c
#include <stdio.h>

int main() {
    printf("First line\n");
    printf("Second line\n");
    printf("Third line\n");
    return 0;
}
```

Output:

```
First line
Second line
Third line
```

The order never changes. The first `printf` runs first, then the second, then the third. This predictable order is one of the reasons C is easy to reason about.

---

## Errors vs warnings

When you write code that the compiler cannot understand, you get an **error**. The compiler stops and refuses to create an executable until you fix it.

A **warning** is the compiler saying, "I can still do this, but something looks fishy." Your program might run, but it may not behave the way you expect. A good habit is to treat warnings as errors and fix them.

---

## Reading a compiler message

Compiler messages usually look scary, but they are actually helpful. Here is an example of a message you might see:

```
lesson.c: In function 'main':
lesson.c:5:5: error: expected ';' before 'return'
```

This tells you:
- The file is `lesson.c`.
- The problem is inside `main`.
- The issue is around line 5, column 5.
- A semicolon is missing before `return`.

The compiler points at the line where it noticed the problem. The real mistake is often on the previous line. In this case, a missing semicolon on line 4 made line 5 fail.

---

## A complete example

```c
#include <stdio.h>

int main() {
    printf("Starting...\n");
    printf("Still running...\n");
    printf("Done!\n");
    return 0;
}
```

Output:

```
Starting...
Still running...
Done!
```

---

## Common beginner mistakes

- **Assuming the computer can guess.** The compiler does not know what you meant. It only knows what you wrote.
- **Ignoring warnings.** They are hints about future bugs.
- **Reading only the last error message.** The first error is usually the root cause; later errors often disappear once you fix it.

---

## Mini exercises

1. Write a program that prints the steps of making tea in order.
2. Remove a semicolon on purpose and read the compiler message. What does it say?
3. Add an extra `printf` between two existing lines and confirm the output order changes.

---

## Recap

- You write source code in `.c` files.
- A compiler translates source code into executable machine code.
- C runs statements from top to bottom inside `main`.
- Errors stop compilation; warnings let it continue but signal possible problems.
- Compiler messages tell you the file, line, and nature of the issue.

Now you understand the journey from your ideas to a running program.