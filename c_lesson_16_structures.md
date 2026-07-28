# Lesson 16: Structures

## What you will learn

- How to group related data into one custom type.
- How to declare and use `struct`.
- How `typedef` makes your code cleaner.
- How to create arrays of structures.

---

## Why structures exist

So far you have used variables that hold one value at a time. But real-world things usually have many properties. A student has a name, an age, and a grade. A book has a title, an author, and a year. A rectangle has a width and a height.

A **structure** lets you bundle related values into a single unit.

---

## Declaring a structure

```c
struct Student {
    char name[50];
    int age;
    float gpa;
};
```

This defines a new type called `struct Student`. It has three members: `name`, `age`, and `gpa`.

---

## Creating and using a structure variable

```c
#include <stdio.h>

struct Student {
    char name[50];
    int age;
    float gpa;
};

int main() {
    struct Student alice;

    // Filling in the members
    snprintf(alice.name, sizeof(alice.name), "Alice");
    alice.age = 21;
    alice.gpa = 3.75;

    printf("Name: %s\n", alice.name);
    printf("Age: %d\n", alice.age);
    printf("GPA: %.2f\n", alice.gpa);

    return 0;
}
```

Output:

```
Name: Alice
Age: 21
GPA: 3.75
```

The dot operator `.` connects the variable name with a member name.

---

## Initializing at declaration

You can fill the structure when you declare it:

```c
struct Student alice = {"Alice", 21, 3.75};
```

The values must be in the same order as the members.

---

## Using `typedef`

Writing `struct Student` every time can feel repetitive. `typedef` lets you give the structure a shorter name.

```c
#include <stdio.h>

typedef struct {
    char name[50];
    int age;
    float gpa;
} Student;

int main() {
    Student alice = {"Alice", 21, 3.75};

    printf("Name: %s\n", alice.name);
    printf("Age: %d\n", alice.age);
    printf("GPA: %.2f\n", alice.gpa);

    return 0;
}
```

Output:

```
Name: Alice
Age: 21
GPA: 3.75
```

Now you can use `Student` directly without the word `struct`.

---

## Arrays of structures

You can create arrays where each element is a structure.

```c
#include <stdio.h>

typedef struct {
    char name[50];
    int age;
} Person;

int main() {
    Person people[3] = {
        {"Alice", 21},
        {"Bob", 25},
        {"Carol", 30}
    };

    for (int i = 0; i < 3; i++) {
        printf("%s is %d years old.\n", people[i].name, people[i].age);
    }

    return 0;
}
```

Output:

```
Alice is 21 years old.
Bob is 25 years old.
Carol is 30 years old.
```

Each element of the array is a whole structure. You use the dot operator to access its members.

---

## Common beginner mistakes

- **Forgetting the semicolon after the closing brace of a structure definition.** It is required.
- **Trying to assign one string member with `=` after initialization.** Use `strcpy` or `snprintf`.
- **Mismatching the order of values during initialization.** The compiler trusts the order you wrote.

---

## Mini exercises

1. Create a `struct` for a book with title, author, and year. Initialize it and print the fields.
2. Create an array of three books and print each one in a loop.
3. Use `typedef` to rename your structure and write the program using the shorter name.

---

## Recap

- A `struct` groups related variables into one type.
- Members are accessed with the dot operator `.`.
- `typedef` lets you create a shorter alias for a structure type.
- You can make arrays of structures.
- Initialize members in the order they were declared.

Structures let you model real-world things with many properties in your programs.