# C Programming Language Cheatsheet

This cheatsheet provides a quick reference to the syntax and commonly used concepts in C programming.

## Table of Contents

1. [Basic Syntax](#basic-syntax)
2. [Data Types](#data-types)
3. [Variables](#variables)
4. [Operators](#operators)
5. [Control Flow](#control-flow)
6. [Functions](#functions)
7. [Arrays](#arrays)
8. [Pointers](#pointers)
9. [Strings](#strings)
10. [Structures](#structures)
11. [Memory Management](#memory-management)
12. [File Handling](#file-handling)
13. [Preprocessor Directives](#preprocessor-directives)
14. [Common Functions](#common-functions)
15. [Error Handling](#error-handling)

---

## Basic Syntax

### Structure of a C Program
A C program typically starts with `#include` directives to include necessary header files, followed by the `main` function where the execution begins.

```c
#include <stdio.h>

int main() {
    // Code goes here
    return 0;
}
```

### Comments
Comments are used to explain the code and are ignored by the compiler.

- **Single-line comment**: `// This is a comment`
- **Multi-line comment**: 
  ```c
  /* This is a
     multi-line comment */
  ```

---

## Data Types
Data types specify the type of data that a variable can hold.

- **int**: Integer (e.g., `int age = 25;`)
- **float**: Floating point number (e.g., `float price = 12.99;`)
- **double**: Double precision floating-point number
- **char**: Single character (e.g., `char grade = 'A';`)
- **void**: Function that does not return a value

---

## Variables

### Declaring Variables
Variables must be declared before they are used.

```c
int age;
float height;
char grade;
```

### Initializing Variables
Variables can be initialized at the time of declaration.

```c
int age = 25;
float height = 5.9;
char grade = 'A';
```

---

## Operators

### Arithmetic Operators
Used to perform basic arithmetic operations.

```c
+   // Addition
-   // Subtraction
*   // Multiplication
/   // Division
%   // Modulus (remainder)
```

### Relational Operators
Used to compare two values.

```c
==  // Equal to
!=  // Not equal to
>   // Greater than
<   // Less than
>=  // Greater than or equal to
<=  // Less than or equal to
```

### Logical Operators
Used to perform logical operations.

```c
&&  // Logical AND
||  // Logical OR
!   // Logical NOT
```

### Assignment Operators
Used to assign values to variables.

```c
=   // Simple assignment
+=  // Add and assign
-=  // Subtract and assign
*=  // Multiply and assign
/=  // Divide and assign
%=  // Modulus and assign
```

### Increment/Decrement Operators
Used to increase or decrease the value of a variable by 1.

```c
++  // Increment by 1
--  // Decrement by 1
```

---

## Control Flow

### if-else Statement
Used to execute code based on a condition.

```c
if (condition) {
    // code if true
} else {
    // code if false
}
```

### switch Statement
Used to execute one code block from multiple options.

```c
switch (expression) {
    case value1:
        // code for value1
        break;
    case value2:
        // code for value2
        break;
    default:
        // default code
}
```

### Loops
Loops are used to execute a block of code repeatedly.

#### for Loop
Executes a block of code a specific number of times.

```c
for (int i = 0; i < 10; i++) {
    // code
}
```

#### while Loop
Executes a block of code as long as a condition is true.

```c
while (condition) {
    // code
}
```

#### do-while Loop
Executes a block of code at least once, and then repeatedly executes the block as long as a condition is true.

```c
do {
    // code
} while (condition);
```

---

## Functions

### Declaring Functions
Functions are blocks of code that perform a specific task.

```c
return_type function_name(parameters) {
    // function body
}
```

Example:

```c
int add(int a, int b) {
    return a + b;
}
```

### Calling Functions
Functions are called by their name followed by arguments in parentheses.

```c
int result = add(2, 3);
```

---

## Arrays

### Declaring Arrays
Arrays are used to store multiple values of the same type.

```c
int numbers[5];  // Array of integers
char name[10];   // Array of characters (string)
```

### Initializing Arrays
Arrays can be initialized at the time of declaration.

```c
int numbers[5] = {1, 2, 3, 4, 5};
char name[] = "Hello";  // Implicit size
```

### Accessing Array Elements
Array elements are accessed using their index.

```c
numbers[0] = 10;  // Assigning a value to the first element
printf("%d", numbers[0]);  // Printing the first element
```

---

## Pointers

### Declaring Pointers
Pointers are variables that store the address of another variable.

```c
int x = 10;
int *ptr = &x;  // Pointer to integer
```

### Dereferencing Pointers
Dereferencing a pointer means accessing the value stored at the address the pointer is pointing to.

```c
printf("%d", *ptr);  // Dereferencing to get the value of x
```

---

## Strings

In C, strings are arrays of characters (`char[]`) terminated by a null character `'\0'`.

### Declaring Strings
Strings can be declared with a specific size or initialized with a value.

```c
char name[20];        // Declaration with size
char name[] = "John"; // Implicit size
```

### Accessing String Elements
String elements are accessed using their index.

```c
printf("%c", name[0]);  // Access first character of the string
```

### String Functions (from `string.h`)
Commonly used string functions.

```c
strlen(str);   // Length of the string
strcpy(dest, src);  // Copy string
strcat(dest, src);  // Concatenate strings
strcmp(str1, str2); // Compare strings
```

---

## Structures

### Declaring Structures
Structures are used to group different data types together.

```c
struct Person {
    char name[50];
    int age;
};
```

### Accessing Structure Members
Structure members are accessed using the dot operator.

```c
struct Person p1;
strcpy(p1.name, "John");
p1.age = 30;
```

---

## Memory Management

### malloc and free
`malloc` is used to allocate memory dynamically, and `free` is used to deallocate memory.

```c
int *ptr = (int*)malloc(sizeof(int) * 10);  // Dynamically allocate memory for 10 integers
free(ptr);  // Deallocate memory
```

### calloc and realloc
`calloc` is used to allocate and initialize memory, and `realloc` is used to resize allocated memory.

```c
int *arr = (int*)calloc(5, sizeof(int));  // Allocate and initialize to 0
arr = (int*)realloc(arr, sizeof(int) * 10);  // Resize allocated memory
```

---

## File Handling

### Opening Files
Files are opened using the `fopen` function.

```c
FILE *f = fopen("file.txt", "r");  // Open file for reading
```

### Reading and Writing to Files
Files are read and written using `fscanf` and `fprintf`.

```c
fprintf(f, "Hello, World!");  // Write to file
fscanf(f, "%d", &num);        // Read from file
```

### Closing Files
Files are closed using the `fclose` function.

```c
fclose(f);
```

---

## Preprocessor Directives

### Include Header Files
Header files are included using the `#include` directive.

```c
#include <stdio.h>  // Standard input-output functions
#include <stdlib.h> // Standard library functions
```

### Define Constants
Constants are defined using the `#define` directive.

```c
#define PI 3.14159
```

### Conditional Compilation
Conditional compilation is used to compile code selectively.

```c
#ifdef DEBUG
    printf("Debug mode");
#endif
```

---

## Common Functions

- **printf()**: Print to console
- **scanf()**: Read input from user
- **strlen()**: Get string length
- **strcpy()**: Copy strings
- **malloc()**: Allocate memory
- **free()**: Deallocate memory

---

## Error Handling

- **exit()**: Exit program with a status code
  ```c
  exit(1);  // Exit with error code 1
  ```

- **assert()**: Check assumptions during runtime
  ```c
  assert(x > 0);  // Program stops if condition is false
  ```

- **errno**: Standard error codes (e.g., `errno = 2` for "No such file or directory")
  ```c
  if (fopen("file.txt", "r") == NULL) {
      perror("Error opening file");
  }
  ```

---

## Conclusion

This cheatsheet provides a concise reference to the most commonly used syntax and concepts in C programming. Keep it handy while coding for quick lookups and reminders!