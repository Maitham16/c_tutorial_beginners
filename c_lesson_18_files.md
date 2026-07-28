# Lesson 18: Working with Files

## What you will learn

- How to open, read, write, and close files in C.
- What text files and binary files are.
- How to check for errors when working with files.
- Why you should always close files when you are done.

---

## Why files matter

Variables disappear when the program ends. If you want to keep data after the program closes, you write it to a file. Files let you save settings, logs, documents, and anything else you want to remember.

---

## Opening a file

C uses a `FILE*` pointer to represent an open file. You open a file with `fopen`.

```c
FILE *file = fopen("notes.txt", "w");
```

The second argument is the mode:

| Mode | Meaning |
|------|---------|
| `"r"` | Read. The file must exist. |
| `"w"` | Write. Creates a new file or overwrites an existing one. |
| `"a"` | Append. Adds to the end of an existing file or creates one. |
| `"r+"` | Read and write. The file must exist. |
| `"w+"` | Read and write. Creates or overwrites. |

If `fopen` cannot open the file, it returns `NULL`. Always check for this.

---

## Writing to a file

Use `fprintf` to write formatted text. It works like `printf`, but sends output to a file.

```c
#include <stdio.h>

int main() {
    FILE *file = fopen("notes.txt", "w");

    if (file == NULL) {
        printf("Could not open the file.\n");
        return 1;
    }

    fprintf(file, "This is my first file.\n");
    fprintf(file, "C is powerful.\n");

    fclose(file);

    printf("File written successfully.\n");

    return 0;
}
```

Output:

```
File written successfully.
```

The file `notes.txt` now contains:

```
This is my first file.
C is powerful.
```

---

## Reading from a file

Use `fscanf` to read formatted data or `fgets` to read an entire line.

### Reading a line with `fgets`

```c
#include <stdio.h>

int main() {
    FILE *file = fopen("notes.txt", "r");

    if (file == NULL) {
        printf("Could not open the file.\n");
        return 1;
    }

    char line[100];

    while (fgets(line, sizeof(line), file) != NULL) {
        printf("%s", line);
    }

    fclose(file);

    return 0;
}
```

Output:

```
This is my first file.
C is powerful.
```

`fgets` reads up to one line at a time. It returns `NULL` when there is nothing more to read.

---

## Reading formatted data with `fscanf`

```c
#include <stdio.h>

int main() {
    FILE *file = fopen("data.txt", "r");

    if (file == NULL) {
        printf("Could not open the file.\n");
        return 1;
    }

    char name[50];
    int age;

    while (fscanf(file, "%s %d", name, &age) == 2) {
        printf("Name: %s, Age: %d\n", name, age);
    }

    fclose(file);

    return 0;
}
```

If `data.txt` contains:

```
Alice 21
Bob 25
```

The output is:

```
Name: Alice, Age: 21
Name: Bob, Age: 25
```

`fscanf` returns the number of values successfully read. The loop continues as long as it reads two values.

---

## Closing files

Always call `fclose` when you are done with a file. It flushes any remaining data to disk and frees resources. Forgetting to close a file can cause lost data, especially when writing.

---

## Text files vs binary files

A **text file** stores data as human-readable characters, like the files we have used so far. A **binary file** stores data in the computer's native format. Binary files are smaller and faster for programs, but you cannot read them with a normal text editor.

For now, focus on text files. They are easier to inspect and debug.

---

## Common beginner mistakes

- **Forgetting to check if `fopen` returned `NULL`.** The file may not exist or may be locked.
- **Using the wrong mode.** `"w"` will overwrite existing data without asking.
- **Forgetting to close the file.** This can cause data loss.
- **Reading with `fscanf` without checking the return value.** The program may loop forever or read garbage.

---

## Mini exercises

1. Write a program that writes five lines of a poem to a file.
2. Read that file back and print it to the screen.
3. Create a file with names and scores, then read and print them in a loop.

---

## Recap

- Use `fopen` to open a file and always check for `NULL`.
- Use `fprintf` to write text and `fgets` or `fscanf` to read text.
- Use `fclose` when you are done.
- Text files are human-readable; binary files store data in native format.
- Handle file errors gracefully.

File handling turns your programs from temporary toys into tools that can keep and share information.