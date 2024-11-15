# C Programming Language Documentation

C is a general-purpose, procedural programming language that has been widely used for system programming and software development. This documentation will guide you through the key features, syntax, and concepts of C programming.

## Table of Contents

1. [Introduction](#introduction)
2. [Data Types](#data-types)
3. [Variables and Constants](#variables-and-constants)
4. [Operators](#operators)
5. [Control Structures](#control-structures)
6. [Functions](#functions)
7. [Arrays](#arrays)
8. [Pointers](#pointers)
9. [Structures](#structures)
10. [Input and Output](#input-and-output)
11. [Memory Management](#memory-management)
12. [File Handling](#file-handling)
13. [Preprocessor Directives](#preprocessor-directives)
14. [Common Errors](#common-errors)
15. [Best Practices](#best-practices)

---

## Introduction

C was developed by Dennis Ritchie in the 1970s at Bell Labs. It is a structured, procedural language designed to produce efficient programs. C is a foundational language that has influenced many modern programming languages such as C++, Java, and Python.

## Data Types

C supports the following primary data types:

- **int**: Integer type, used to store whole numbers.
- **float**: Used for floating-point numbers (decimal values).
- **double**: Double precision floating-point numbers.
- **char**: Used for storing single characters.
  
C also supports derived types such as:

- **Array**: A collection of data items of the same type.
- **Pointer**: A variable that stores the memory address of another variable.
- **Structure**: A collection of variables of different types.

### Size of Data Types (varies by system)
- `int`: 4 bytes
- `float`: 4 bytes
- `double`: 8 bytes
- `char`: 1 byte

## Variables and Constants

### Declaring Variables

To declare a variable in C, specify the type followed by the variable name:
```c
int age;
float salary;
char grade;
```

### Constants

Constants are values that cannot be changed during program execution. They can be declared using the `#define` preprocessor directive:
```c
#define PI 3.14159
```

## Operators

C includes a wide variety of operators, such as:

- **Arithmetic Operators**: `+`, `-`, `*`, `/`, `%`
- **Relational Operators**: `==`, `!=`, `>`, `<`, `>=`, `<=`
- **Logical Operators**: `&&`, `||`, `!`
- **Bitwise Operators**: `&`, `|`, `^`, `<<`, `>>`
- **Assignment Operators**: `=`, `+=`, `-=`, `*=`, `/=`
- **Increment/Decrement Operators**: `++`, `--`

## Control Structures

Control structures in C allow you to control the flow of the program based on conditions.

### Conditional Statements

- **if**: Executes a block of code if the condition is true.
- **else**: Executes a block of code if the condition is false.
- **else if**: Provides additional conditions after an initial `if`.

```c
if (x > 10) {
    printf("x is greater than 10");
} else {
    printf("x is less than or equal to 10");
}
```

### Switch Statement

Used to select one of many code blocks to execute:
```c
switch (x) {
    case 1:
        printf("One");
        break;
    case 2:
        printf("Two");
        break;
    default:
        printf("Other");
}
```

### Loops

- **for** loop: Executes a block of code a specific number of times.
- **while** loop: Executes as long as the condition is true.
- **do-while** loop: Executes at least once before checking the condition.

```c
for (int i = 0; i < 10; i++) {
    printf("%d\n", i);
}
```

## Functions

Functions in C are used to break a program into smaller, modular pieces.

### Declaring Functions

A function in C is declared with a return type, function name, and parameters:
```c
int add(int a, int b) {
    return a + b;
}
```

Functions can return values or be `void` (return nothing).

### Function Call

To call a function, use its name followed by arguments (if any):
```c
int result = add(2, 3);
```

## Arrays

An array is a collection of variables of the same type.

### Declaring an Array

```c
int numbers[5];  // Array of 5 integers
```

### Accessing Array Elements

```c
numbers[0] = 10;  // Assign value to the first element
printf("%d", numbers[0]);  // Access the first element
```

## Pointers

A pointer is a variable that stores the memory address of another variable.

### Declaring Pointers

```c
int num = 10;
int *ptr = &num;
```

### Dereferencing Pointers

Use the `*` operator to dereference a pointer and access the value stored at that address:
```c
printf("%d", *ptr);  // Prints 10
```

## Structures

A structure is a user-defined data type that allows grouping variables of different types.

### Declaring a Structure

```c
struct Person {
    char name[50];
    int age;
};
```

### Accessing Structure Members

```c
struct Person p1;
strcpy(p1.name, "John");
p1.age = 30;
```

## Input and Output

C uses standard libraries for input and output operations.

- **`printf()`**: Used for printing to the console.
- **`scanf()`**: Used for reading input from the user.

```c
int num;
printf("Enter a number: ");
scanf("%d", &num);
```

## Memory Management

C provides functions for dynamic memory management:
- **malloc()**: Allocates memory at runtime.
- **free()**: Deallocates memory that was previously allocated.

```c
int *arr = (int *)malloc(10 * sizeof(int));  // Allocate memory
free(arr);  // Free the allocated memory
```

## File Handling

C provides functions for reading from and writing to files.

- **`fopen()`**: Opens a file.
- **`fprintf()`**: Writes formatted output to a file.
- **`fscanf()`**: Reads formatted input from a file.
- **`fclose()`**: Closes an opened file.

```c
FILE *file = fopen("example.txt", "w");
fprintf(file, "Hello, World!\n");
fclose(file);
```

## Preprocessor Directives

C includes preprocessor directives that are used to modify the program before compilation:

- **`#include`**: Includes a header file.
- **`#define`**: Defines constants or macros.
- **`#ifdef`, `#ifndef`, `#endif`**: Conditional compilation.

```c
#include <stdio.h>
#define PI 3.14159
```

## Common Errors

Some common errors in C programming include:

- **Syntax Errors**: Missing semicolons, parentheses, or braces.
- **Segmentation Faults**: Invalid memory access, often due to dereferencing null or uninitialized pointers.
- **Buffer Overflow**: Writing past the end of an array or buffer.

## Best Practices

- Always initialize variables before use.
- Use meaningful variable names.
- Avoid using "magic numbers" (literal values in code); use constants instead.
- Use functions to modularize code.
- Avoid global variables; prefer passing arguments to functions.
- Always free dynamically allocated memory.

---

## Conclusion

C is a powerful, efficient, and versatile language, making it a popular choice for system-level programming, embedded systems, and high-performance applications. By understanding its syntax, features, and best practices, you can write effective and optimized C programs.
```

This markdown file provides an overview of the essentials for C programming.