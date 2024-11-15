# C++ Programming Language Cheatsheet

This cheatsheet provides a quick reference to the most important concepts, syntax, and features in C++ programming.

## Table of Contents

1. [Basic Syntax](#basic-syntax)
2. [Data Types](#data-types)
3. [Variables](#variables)
4. [Operators](#operators)
5. [Control Flow](#control-flow)
6. [Functions](#functions)
7. [Classes and Objects](#classes-and-objects)
8. [Memory Management](#memory-management)
9. [Pointers and References](#pointers-and-references)
10. [Arrays and Vectors](#arrays-and-vectors)
11. [Strings](#strings)
12. [File Handling](#file-handling)
13. [Exception Handling](#exception-handling)
14. [Templates](#templates)
15. [STL (Standard Template Library)](#stl-standard-template-library)
16. [Common Functions](#common-functions)
17. [Best Practices](#best-practices)

---

## Basic Syntax

### Structure of a C++ Program

```cpp
#include <iostream>
using namespace std;

int main() {
    // Code goes here
    cout << "Hello, World!" << endl;
    return 0;
}
```

### Comments

- **Single-line comment**: `// This is a comment`
- **Multi-line comment**: 
  ```cpp
  /* This is a
     multi-line comment */
  ```

---

## Data Types

- **int**: Integer (e.g., `int x = 10;`)
- **float**: Floating point number (e.g., `float x = 10.5f;`)
- **double**: Double precision floating point (e.g., `double x = 10.5555;`)
- **char**: Single character (e.g., `char grade = 'A';`)
- **bool**: Boolean (e.g., `bool isActive = true;`)
- **string**: String (requires `#include <string>`)
- **void**: No return type (used for functions that don’t return a value)

---

## Variables

### Declaring Variables

```cpp
int x;             // Integer
float y;           // Float
double z;          // Double
char letter;       // Character
bool flag;         // Boolean
string name;       // String (requires #include <string>)
```

### Initializing Variables

```cpp
int x = 10;
float y = 5.75;
string name = "John";
```

---

## Operators

### Arithmetic Operators

```cpp
+   // Addition
-   // Subtraction
*   // Multiplication
/   // Division
%   // Modulus (remainder)
```

### Relational Operators

```cpp
==  // Equal to
!=  // Not equal to
>   // Greater than
<   // Less than
>=  // Greater than or equal to
<=  // Less than or equal to
```

### Logical Operators

```cpp
&&  // Logical AND
||  // Logical OR
!   // Logical NOT
```

### Assignment Operators

```cpp
=   // Simple assignment
+=  // Add and assign
-=  // Subtract and assign
*=  // Multiply and assign
/=  // Divide and assign
%=  // Modulus and assign
```

### Increment and Decrement Operators

```cpp
++  // Increment by 1
--  // Decrement by 1
```

---

## Control Flow

### if-else Statement

```cpp
if (condition) {
    // code if true
} else {
    // code if false
}
```

### switch Statement

```cpp
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

```cpp
for (int i = 0; i < 10; i++) {
    cout << i << endl;
}
```

#### while Loop

```cpp
int i = 0;
while (i < 10) {
    cout << i << endl;
    i++;
}
```

#### do-while Loop

```cpp
int i = 0;
do {
    cout << i << endl;
    i++;
} while (i < 10);
```

---

## Functions

### Declaring Functions

```cpp
return_type function_name(parameters) {
    // function body
}
```

Example:

```cpp
int add(int a, int b) {
    return a + b;
}
```

### Calling Functions

```cpp
int result = add(3, 4);
cout << result;  // Output: 7
```

### Function Overloading

```cpp
int add(int a, int b) { return a + b; }
double add(double a, double b) { return a + b; }
```

### Default Arguments

```cpp
int add(int a, int b = 5) { return a + b; }  // b has a default value of 5
```

---

## Classes and Objects

### Declaring a Class

```cpp
class Person {
public:
    string name;
    int age;

    void greet() {
        cout << "Hello, my name is " << name << " and I am " << age << " years old." << endl;
    }
};
```

### Creating an Object

```cpp
Person person1;
person1.name = "John";
person1.age = 30;
person1.greet();
```

### Constructor and Destructor

```cpp
class Person {
public:
    string name;
    int age;

    // Constructor
    Person(string n, int a) {
        name = n;
        age = a;
    }

    // Destructor
    ~Person() {
        cout << "Object is being deleted" << endl;
    }
};
```

---

## Memory Management

### Dynamically Allocating Memory

```cpp
int* ptr = new int;  // Allocates memory for one integer
*ptr = 10;
cout << *ptr;    // Dereferencing the pointer, Output: 10
```

### Deallocating Memory

```cpp
delete ptr;  // Deallocates memory
```

### Array Allocation

```cpp
int* arr = new int[10];  // Allocates memory for an array of 10 integers
arr[0] = 5;
delete[] arr;  // Deallocates memory
```

---

## Pointers and References

### Pointers

```cpp
int x = 10;
int* ptr = &x;  // Pointer to x
cout << *ptr;    // Dereferencing the pointer, Output: 10
```

### References

```cpp
int x = 10;
int& ref = x;  // Reference to x
ref = 20;      // Changing ref also changes x
cout << x;     // Output: 20
```

### Pointer Arithmetic

```cpp
int arr[] = {1, 2, 3};
int* ptr = arr;
cout << *(ptr + 1);  // Output: 2
```

---

## Arrays and Vectors

### Declaring an Array

```cpp
int arr[5] = {1, 2, 3, 4, 5};
```

### Accessing Array Elements

```cpp
cout << arr[0];  // Output: 1
```

### Vectors (Dynamic Arrays)

```cpp
#include <vector>

vector<int> vec;
vec.push_back(10);  // Adding an element
cout << vec[0];     // Output: 10
```

---

## Strings

### Declaring a String

```cpp
string name = "John";  // String from std::string class
```

### String Functions

```cpp
cout << name.length();       // Length of string
cout << name.substr(0, 4);   // Substring (First 4 characters)
cout << name.find("oh");     // Find substring (returns position)
```

### C-style String

```cpp
char name[] = "John";  // Null-terminated string (C-style)
```

---

## File Handling

### Opening Files

```cpp
#include <fstream>
ofstream outfile("example.txt");
ifstream infile("example.txt");
```

### Writing to Files

```cpp
outfile << "Hello, World!" << endl;
outfile.close();
```

### Reading from Files

```cpp
string line;
while (getline(infile, line)) {
    cout << line << endl;
}
infile.close();
```

---

## Exception Handling

### try-catch Block

```cpp
try {
    int x = 5 / 0;  // Will throw an exception
} catch (const exception& e) {
    cout << "Error: " << e.what() << endl;
}
```

### try-catch-finally Block

```cpp
try {
    int x = 5 / 0;  // Will throw an exception
} catch (const exception& e) {
    cout << "Error: " << e.what() << endl;
} finally {
    cout << "Execution completed." << endl;
}
```

---

## Templates

### Function Templates

```cpp
template <typename T>
T add(T a, T b

) {
    return a + b;
}
```

### Class Templates

```cpp
template <class T>
class Box {
public:
    T value;
    Box(T val) : value(val) {}
    T getValue() {
        return value;
    }
};
```

---

## STL (Standard Template Library)

### Vectors

```cpp
#include <vector>
vector<int> vec = {1, 2, 3, 4};
vec.push_back(5);
```

### Maps (Key-Value Pairs)

```cpp
#include <map>
map<string, int> age;
age["John"] = 25;
cout << age["John"];  // Output: 25
```

### Sets (Unique Elements)

```cpp
#include <set>
set<int> numbers = {1, 2, 3};
numbers.insert(4);
```

### Iterators

```cpp
#include <vector>
vector<int> vec = {1, 2, 3};
for (auto it = vec.begin(); it != vec.end(); ++it) {
    cout << *it << endl;
}
```

---

## Common Functions

- **cout**: Output to console
- **cin**: Input from console
- **getline()**: Read an entire line of text
- **sort()**: Sort elements (requires `<algorithm>` header)
- **reverse()**: Reverse a container
- **max()**, **min()**: Find the largest or smallest value
- **swap()**: Swap two values

---

## Best Practices

- Use **camelCase** for variable and function names.
- Follow the **RAII** (Resource Acquisition Is Initialization) pattern for resource management.
- Prefer **const** where applicable to avoid accidental changes.
- Avoid **using namespace std;** in larger projects to prevent naming conflicts.
- Make use of **nullptr** instead of **NULL**.
- Use **auto** to let the compiler infer types when the type is obvious.
- Prefer **reference variables** over pointers where possible for safer code.

---

## Conclusion

This cheatsheet covers the most essential concepts of C++ programming, from basic syntax to advanced features like templates and exception handling. Whether you are a beginner or an experienced developer, this guide should help you quickly reference key syntax and concepts in C++.
```