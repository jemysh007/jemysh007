# C Programming Language Cheatsheet

This cheatsheet provides a quick reference to the syntax and commonly used concepts in C programming.

---

## Basic Syntax

### Structure of a C Program

```c
#include <stdio.h>

int main() {
    // Code goes here
    return 0;
}
```

### Comments

- **Single-line comment**: `// This is a comment`
- **Multi-line comment**: 
  ```c
  /* This is a
     multi-line comment */
  ```

---

## Data Types

- **int**: Integer (e.g., `int age = 25;`)
- **float**: Floating point number (e.g., `float price = 12.99;`)
- **double**: Double precision floating-point number
- **char**: Single character (e.g., `char grade = 'A';`)
- **void**: Function that does not return a value

---

## Variables

### Declaring Variables

```c
int age;
float height;
char grade;
```

### Initializing Variables

```c
int age = 25;
float height = 5.9;
char grade = 'A';
```

---

## Operators

### Arithmetic Operators

```c
+   // Addition
-   // Subtraction
*   // Multiplication
/   // Division
%   // Modulus (remainder)
```

### Relational Operators

```c
==  // Equal to
!=  // Not equal to
>   // Greater than
<   // Less than
>=  // Greater than or equal to
<=  // Less than or equal to
```

### Logical Operators

```c
&&  // Logical AND
||  // Logical OR
!   // Logical NOT
```

### Assignment Operators

```c
=   // Simple assignment
+=  // Add and assign
-=  // Subtract and assign
*=  // Multiply and assign
/=  // Divide and assign
%=  // Modulus and assign
```

### Increment/Decrement Operators

```c
++  // Increment by 1
--  // Decrement by 1
```

---

## Control Flow

### if-else Statement

```c
if (condition) {
    // code if true
} else {
    // code if false
}
```

### switch Statement

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

#### for Loop

```c
for (int i = 0; i < 10; i++) {
    // code
}
```

#### while Loop

```c
while (condition) {
    // code
}
```

#### do-while Loop

```c
do {
    // code
} while (condition);
```

---

## Functions

### Declaring Functions

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

```c
int result = add(2, 3);
```

---

## Arrays

### Declaring Arrays

```c
int numbers[5];  // Array of integers
char name[10];   // Array of characters (string)
```

### Initializing Arrays

```c
int numbers[5] = {1, 2, 3, 4, 5};
char name[] = "Hello";  // Implicit size
```

### Accessing Array Elements

```c
numbers[0] = 10;  // Assigning a value to the first element
printf("%d", numbers[0]);  // Printing the first element
```

---

## Pointers

### Declaring Pointers

```c
int x = 10;
int *ptr = &x;  // Pointer to integer
```

### Dereferencing Pointers

```c
printf("%d", *ptr);  // Dereferencing to get the value of x
```

---

## Strings

In C, strings are arrays of characters (`char[]`) terminated by a null character `'\0'`.

### Declaring Strings

```c
char name[20];        // Declaration with size
char name[] = "John"; // Implicit size
```

### Accessing String Elements

```c
printf("%c", name[0]);  // Access first character of the string
```

### String Functions (from `string.h`)

```c
strlen(str);   // Length of the string
strcpy(dest, src);  // Copy string
strcat(dest, src);  // Concatenate strings
strcmp(str1, str2); // Compare strings
```

---

## Structures

### Declaring Structures

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

---

## Memory Management

### malloc and free

```c
int *ptr = (int*)malloc(sizeof(int) * 10);  // Dynamically allocate memory for 10 integers
free(ptr);  // Deallocate memory
```

### calloc and realloc

```c
int *arr = (int*)calloc(5, sizeof(int));  // Allocate and initialize to 0
arr = (int*)realloc(arr, sizeof(int) * 10);  // Resize allocated memory
```

---

## File Handling

### Opening Files

```c
FILE *f = fopen("file.txt", "r");  // Open file for reading
```

### Reading and Writing to Files

```c
fprintf(f, "Hello, World!");  // Write to file
fscanf(f, "%d", &num);        // Read from file
```

### Closing Files

```c
fclose(f);
```

---

## Preprocessor Directives

### Include Header Files

```c
#include <stdio.h>  // Standard input-output functions
#include <stdlib.h> // Standard library functions
```

### Define Constants

```c
#define PI 3.14159
```

### Conditional Compilation

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
```