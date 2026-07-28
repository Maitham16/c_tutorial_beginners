# Lesson 1: Hello, World!

## What you will learn

- What the C language is and why people still use it.
- How to write, compile, and run your very first C program.
- What `main`, `printf`, and the curly braces really mean.
- Why the semicolon is your new best friend.

---

## Welcome to C

Imagine you are giving instructions to a very fast, very literal, but not very imaginative assistant. That assistant is the computer. C is one of the languages you can use to write those instructions.

C was created in the 1970s, and it is still everywhere today. Your operating system, your phone, your microwave, and many video games all rely on C or languages inspired by it. C is small, fast, and close to the machine, which makes it a great first language if you want to understand how computers actually think.

---

## How to run your first program

You do not need to install anything fancy to start. Open any online C compiler, for example Programiz C Online Compiler or OnlineGDB. You paste your code on the left, click **Run**, and the output appears on the right.

If you later want to compile on your own computer, you can, but an online compiler is perfect for learning.

---

## Your first program

Type this exactly into the editor:

```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

When you run it, you should see:

```
Hello, World!
```

Let us break every line down so it stops looking like magic.

---

## Line by line

### `#include <stdio.h>`

`stdio` stands for **standard input/output**. This line tells the compiler, "I want to use the standard tools for printing text and reading input." `printf` lives inside this library, so without this line the compiler would not know what `printf` is.

### `int main()`

Every C program starts at `main`. It is the front door of your program. The word `int` means that `main` will return an integer number when it finishes. Returning `0` means "everything went fine."

### The curly braces `{` and `}`

Curly braces group code together. Everything inside the braces of `main` belongs to `main`. Think of them as the walls of a room. Right now, the room only has one piece of furniture.

### `printf("Hello, World!\n");`

`printf` prints text to the screen. The text goes inside double quotes. The `\n` at the end means "new line." It is like pressing Enter on your keyboard. If you leave it out, the next thing you print will stick to the same line.

The semicolon `;` at the end is very important. In C, it marks the end of a statement. Forgetting it is like forgetting the period at the end of a sentence. The computer gets confused.

### `return 0;`

This sends the number `0` back to the operating system, which means the program ended successfully. Later you will learn how different return numbers can signal different outcomes.

---

## Try this

Change the message inside the quotes and run it again.

```c
#include <stdio.h>

int main() {
    printf("I am learning C!\n");
    return 0;
}
```

Output:

```
I am learning C!
```

---

## Common beginner mistakes

- **Forgetting the semicolon.** The compiler will complain loudly. If you see an error, check the line above where the error points.
- **Using curly quotes.** Make sure your quotes are straight `"` and not slanted. Slanted quotes come from copying from word processors.
- **Forgetting the closing brace.** Every opening `{` needs a closing `}`.
- **Writing `Print` instead of `printf`.** C is case-sensitive, so `Printf` and `printf` are different things.

---

## Mini exercises

1. Print your name on the screen.
2. Print three separate lines: your favorite food, your favorite color, and your favorite number.
3. What happens if you remove `\n` from all three lines? Predict the output, then try it.

---

## Recap

- A C program is a set of instructions that starts at `main`.
- `#include <stdio.h>` gives you the tools to print text.
- `printf` writes text to the screen.
- Statements end with a semicolon.
- `return 0;` tells the system the program finished successfully.

You have already written and understood a real C program. That is lesson one done.