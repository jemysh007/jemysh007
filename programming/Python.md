# Python Programming Language Documentation

## Table of Contents

1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Basic Syntax](#basic-syntax)
4. [Data Types](#data-types)
    - [Numeric Types](#numeric-types)
    - [Sequence Types](#sequence-types)
    - [Mapping Type](#mapping-type)
    - [Set Types](#set-types)
    - [Text Type](#text-type)
    - [Boolean Type](#boolean-type)
    - [Binary Types](#binary-types)
5. [Control Flow](#control-flow)
6. [Functions](#functions)
7. [Modules and Packages](#modules-and-packages)
8. [Object-Oriented Programming](#object-oriented-programming)
9. [Error Handling](#error-handling)
10. [Libraries and Frameworks](#libraries-and-frameworks)
11. [Best Practices](#best-practices)
12. [Useful Resources](#useful-resources)

## Introduction

Python is an interpreted, high-level, general-purpose programming language that emphasizes readability and simplicity. It supports multiple programming paradigms, including procedural, object-oriented, and functional programming. Python is widely used in various domains such as web development, data science, artificial intelligence, automation, and more.

## Installation

### Prerequisites

- A computer with internet access
- Python 3.7 or higher (recommended)
- A text editor or integrated development environment (IDE) such as VS Code, PyCharm, or Sublime Text

### Steps to Install Python

1. Download Python from the [official website](https://www.python.org/downloads/).
2. Follow the installation instructions specific to your operating system:
   - **Windows**: Run the installer and ensure to check the box to add Python to your system path.
   - **macOS/Linux**: Use package managers like Homebrew (macOS) or apt (Ubuntu) to install Python.
3. Verify installation by running the following command in your terminal or command prompt:
   ```bash
   python --version
   ```

### Installing Dependencies

You can install dependencies (Python packages) via `pip`:
```bash
pip install <package_name>
```

## Basic Syntax

### Comments
Python supports single-line and multi-line comments:

```python
# This is a single-line comment

'''
This is a
multi-line comment
'''
```

### Variables and Data Types

Python is dynamically typed, meaning variables do not need explicit type declarations.

```python
x = 10         # integer
name = "John"  # string
pi = 3.14      # float
is_active = True  # boolean
```

### Indentation

Python uses indentation to define code blocks rather than curly braces `{}`.

```python
if x > 5:
    print("x is greater than 5")
```

## Data Types

Python supports various built-in data types:

### Numeric Types

- **`int`**: Integer numbers, e.g., `10`, `-5`
- **`float`**: Floating point numbers, e.g., `3.14`, `-2.5`
- **`complex`**: Complex numbers, e.g., `2 + 3j`

Example:
```python
integer = 5
floating_point = 3.1415
complex_number = 2 + 3j
```

### Sequence Types

- **`list`**: Ordered, mutable collection of items. Lists can contain items of different data types.
  
  Example:
  ```python
  my_list = [1, 2, 3, "apple", 4.5]
  ```
  
- **`tuple`**: Ordered, immutable collection of items. Once a tuple is created, its contents cannot be modified.
  
  Example:
  ```python
  my_tuple = (1, 2, 3, "apple", 4.5)
  ```
  
- **`range`**: Immutable sequence of numbers, commonly used in loops.
  
  Example:
  ```python
  for i in range(5):
      print(i)
  ```

### Mapping Type

- **`dict`**: Unordered collection of key-value pairs. Keys are unique.
  
  Example:
  ```python
  my_dict = {"name": "John", "age": 30, "city": "New York"}
  ```

### Set Types

- **`set`**: Unordered collection of unique items. Sets do not allow duplicates.
  
  Example:
  ```python
  my_set = {1, 2, 3, 4}
  my_set.add(5)  # Adds an element to the set
  my_set.remove(3)  # Removes an element from the set
  ```

- **`frozenset`**: Immutable version of a set. Once created, the items cannot be changed.
  
  Example:
  ```python
  my_frozenset = frozenset([1, 2, 3, 4])
  ```

### Text Type

- **`str`**: A sequence of characters used to store text. Strings are immutable in Python.
  
  Example:
  ```python
  my_string = "Hello, World!"
  print(my_string.upper())  # Outputs: HELLO, WORLD!
  ```

### Boolean Type

- **`bool`**: Represents `True` or `False` values.
  
  Example:
  ```python
  is_active = True
  is_done = False
  ```

### Binary Types

- **`bytes`**: Immutable sequence of bytes (8-bit values).
  
  Example:
  ```python
  my_bytes = b"hello"
  ```
  
- **`bytearray`**: Mutable version of `bytes`.
  
  Example:
  ```python
  my_bytearray = bytearray([65, 66, 67])
  ```

## Control Flow

### If-Else Statements

```python
x = 10
if x > 5:
    print("x is greater than 5")
else:
    print("x is less than or equal to 5")
```

### Loops

#### For Loop
```python
for i in range(5):
    print(i)
```

#### While Loop
```python
x = 0
while x < 5:
    print(x)
    x += 1
```

## Functions

Functions are defined using the `def` keyword:

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))
```

### Lambda Functions

Lambda functions are anonymous functions:

```python
add = lambda x, y: x + y
print(add(2, 3))
```

## Modules and Packages

### Importing Modules

You can import built-in or third-party modules.

```python
import math
print(math.sqrt(16))
```

### Creating Custom Modules

Save your code in a `.py` file and import it as a module.

Example `greetings.py`:
```python
def say_hello(name):
    return f"Hello, {name}!"
```

```python
import greetings
print(greetings.say_hello("John"))
```

## Object-Oriented Programming

### Classes and Objects

Python supports object-oriented programming (OOP).

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hello, my name is {self.name} and I am {self.age} years old."

# Creating an object
person = Person("Alice", 30)
print(person.greet())
```

### Inheritance

```python
class Employee(Person):
    def __init__(self, name, age, job_title):
        super().__init__(name, age)
        self.job_title = job_title

    def work(self):
        return f"{self.name} is working as {self.job_title}."

# Creating an object of the child class
employee = Employee("Bob", 35, "Software Engineer")
print(employee.work())
```

## Error Handling

Python uses `try`, `except`, `else`, and `finally` for error handling.

```python
try:
    x = 10 / 0
except ZeroDivisionError:
    print("You cannot divide by zero!")
else:
    print("No errors occurred.")
finally:
    print("This will always execute.")
```

## Libraries and Frameworks

### Popular Libraries

- **NumPy**: Numerical computations
- **Pandas**: Data analysis and manipulation
- **Requests**: HTTP requests
- **Matplotlib**: Plotting and visualization
- **Flask/Django**: Web frameworks
- **TensorFlow/Keras**: Machine learning and deep learning

### Installing Libraries
You can install libraries using `pip`:

```bash
pip install numpy pandas requests
```

## Best Practices

- **Follow PEP 8**: Python's official style guide for clean and readable code.
- **Use Virtual Environments**: Isolate project dependencies using `venv` or `virtualenv`.
- **Write Unit Tests**: Use frameworks like `unittest` or `pytest` for testing your code.
- **Document Your Code**: Use docstrings for functions and classes to provide context.

## Useful Resources

- [Official Python Documentation](https://docs.python.org/3/)
- [Python Package Index (PyPI)](https://pypi.org/)
- [

Real Python](https://realpython.com/)
```