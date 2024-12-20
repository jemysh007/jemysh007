# Python Cheatsheet: Useful Functions and Libraries

## Table of Contents
1. [Basic Syntax & Constants](#1-basic-syntax--constants)
2. [Data Types](#2-data-types)
3. [String Manipulation](#3-string-manipulation)
4. [Lists](#4-lists)
5. [Tuples](#5-tuples)
6. [Dictionaries](#6-dictionaries)
7. [Sets](#7-sets)
8. [Functions](#8-functions)
9. [Lambda Functions](#9-lambda-functions)
10. [Loops](#10-loops)
11. [Conditionals](#11-conditionals)
12. [Comprehensions](#12-comprehensions)
13. [File Operations](#13-file-operations)
14. [Date and Time](#14-date-and-time)
15. [Error Handling](#15-error-handling)
16. [Modules and Packages](#16-modules-and-packages)
17. [Regular Expressions](#17-regular-expressions)
18. [Iterators and Generators](#18-iterators-and-generators)
19. [Object-Oriented Programming (OOP)](#19-object-oriented-programming-oop)
20. [Popular Libraries](#20-popular-libraries)

---

## 1. **Basic Syntax & Constants**

### 1.1 **Printing Output**

The `print` function is used to output text or variables to the console.

```python
print("Hello, World!")
```

### 1.2 **Comments**

Comments are used to explain code and are ignored by the interpreter.

```python
# This is a single-line comment

'''
This is a
multi-line comment
'''
```

### 1.3 **Constants**

Python doesn’t have built-in constants, but you can define them in uppercase to indicate they should not be changed.

```python
PI = 3.14159
```

---

## 2. **Data Types**

Python supports various data types to store different kinds of data.

### 2.1 **Numbers**

```python
x = 10            # Integer
y = 3.14          # Float
z = 2 + 3j        # Complex number
```

### 2.2 **Strings**

Strings are sequences of characters enclosed in quotes.

```python
s = "Hello, Python!"
```

### 2.3 **Booleans**

Booleans represent `True` or `False` values.

```python
is_active = True
is_done = False
```

### 2.4 **Lists**

Lists are ordered collections of items that can be of different types.

```python
my_list = [1, 2, 3, "apple", 5.6]
```

### 2.5 **Tuples**

Tuples are ordered collections of items that are immutable.

```python
my_tuple = (1, 2, 3)
```

### 2.6 **Dictionaries**

Dictionaries are collections of key-value pairs.

```python
my_dict = {"name": "John", "age": 30}
```

### 2.7 **Sets**

Sets are unordered collections of unique items.

```python
my_set = {1, 2, 3, 4}
```

---

## 3. **String Manipulation**

### 3.1 **Length of String**

The `len` function returns the length of a string.

```python
len("Hello")  # Outputs: 5
```

### 3.2 **String Slicing**

String slicing allows you to access a substring.

```python
s = "Hello"
print(s[1:4])  # Outputs: ell
```

### 3.3 **Convert to Upper/Lower**

You can convert a string to uppercase or lowercase using the `upper` and `lower` methods.

```python
s = "hello"
print(s.upper())  # Outputs: HELLO
print(s.lower())  # Outputs: hello
```

### 3.4 **String Concatenation**

String concatenation combines two or more strings.

```python
greeting = "Hello"
name = "John"
print(greeting + " " + name)  # Outputs: Hello John
```

---

## 4. **Lists**

### 4.1 **List Access & Modification**

Lists are mutable, meaning you can change their elements.

```python
my_list = [1, 2, 3, "apple"]
my_list[0] = 10  # Modify first element
print(my_list)  # Outputs: [10, 2, 3, 'apple']
```

### 4.2 **List Append**

The `append` method adds an element to the end of the list.

```python
my_list.append(4)
print(my_list)  # Outputs: [10, 2, 3, 'apple', 4]
```

### 4.3 **List Remove**

The `remove` method removes the first occurrence of a specified value.

```python
my_list.remove("apple")
print(my_list)  # Outputs: [10, 2, 3, 4]
```

---

## 5. **Tuples**

### 5.1 **Accessing Tuple Elements**

You can access elements in a tuple using indexing.

```python
my_tuple = (1, 2, 3)
print(my_tuple[0])  # Outputs: 1
```

### 5.2 **Immutability of Tuples**

Tuples are immutable, meaning their elements cannot be changed.

```python
# You cannot change an element in a tuple
# my_tuple[0] = 10  # This will raise an error
```

---

## 6. **Dictionaries**

### 6.1 **Accessing Dictionary Elements**

You can access dictionary values using their keys.

```python
my_dict = {"name": "John", "age": 30}
print(my_dict["name"])  # Outputs: John
```

### 6.2 **Adding/Updating Key-Value Pairs**

You can add or update key-value pairs in a dictionary.

```python
my_dict["location"] = "New York"
print(my_dict)  # Outputs: {'name': 'John', 'age': 30, 'location': 'New York'}
```

### 6.3 **Removing Items**

You can remove items from a dictionary using the `del` statement.

```python
del my_dict["age"]
print(my_dict)  # Outputs: {'name': 'John', 'location': 'New York'}
```

---

## 7. **Sets**

### 7.1 **Creating and Modifying Sets**

Sets are mutable, and you can add items using the `add` method.

```python
my_set = {1, 2, 3}
my_set.add(4)  # Add item
print(my_set)  # Outputs: {1, 2, 3, 4}
```

### 7.2 **Set Operations**

Sets support mathematical operations like union and intersection.

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
print(set1 & set2)  # Intersection: {3}
print(set1 | set2)  # Union: {1, 2, 3, 4, 5}
```

---

## 8. **Functions**

### 8.1 **Defining a Function**

Functions are defined using the `def` keyword.

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))  # Outputs: Hello, Alice!
```

### 8.2 **Default Parameters**

Functions can have default parameter values.

```python
def greet(name="World"):
    return f"Hello, {name}!"

print(greet())  # Outputs: Hello, World!
```

---

## 9. **Lambda Functions**

### 9.1 **Defining a Lambda Function**

Lambda functions are anonymous functions defined using the `lambda` keyword.

```python
add = lambda x, y: x + y
print(add(5, 3))  # Outputs: 8
```

---

## 10. **Loops**

### 10.1 **For Loop**

For loops are used to iterate over a sequence.

```python
for i in range(3):
    print(i)  # Outputs: 0 1 2
```

### 10.2 **While Loop**

While loops are used to execute a block of code as long as a condition is true.

```python
i = 0
while i < 3:
    print(i)  # Outputs: 0 1 2
    i += 1
```

---

## 11. **Conditionals**

### 11.1 **If-Else Statement**

If-else statements are used to execute code based on conditions.

```python
x = 10
if x > 5:
    print("Greater than 5")  # Outputs: Greater than 5
else:
    print("Less than or equal to 5")
```

---

## 12. **Comprehensions**

### 12.1 **List Comprehension**

List comprehensions provide a concise way to create lists.

```python
squares = [x**2 for x in range(5)]
print(squares)  # Outputs: [0, 1, 4, 9, 16]
```

### 12.2 **Dictionary Comprehension**

Dictionary comprehensions provide a concise way to create dictionaries.

```python
squares_dict = {x: x**2 for x in range(5)}
print(squares_dict)  # Outputs: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

---

## 13. **File Operations**

### 13.1 **Reading a File**

You can read the contents of a file using the `open` function and a context manager.

```python
with open('file.txt', 'r') as file:
    content = file.read()
    print(content)
```

### 13.2 **Writing to a File**

You can write to a file using the `open` function and a context manager.

```python
with open('file.txt', 'w') as file:
    file.write("Hello, World!")
```

---

## 14. **Date and Time**

### 14.1 **Get Current Date and Time**

You can get the current date and time using the `datetime` module.

```python
import datetime
now = datetime.datetime.now()
print(now)  # Outputs: current date and time
```

### 14.2 **Format Date**

You can format dates using the `strftime` method.

```python
print(now.strftime("%Y-%m-%d %H:%M:%S"))  # Outputs: 2024-11-18 12:45:00
```

---

## 15. **Error Handling**

### 15.1 **Try-Except Block**

Try-except blocks are used to handle exceptions.

```python
try:
    x = 1 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

---

## 16. **Modules and Packages**

### 16.1 **Importing a Module**

You can import modules using the `import` statement.

```python
import math
print(math.sqrt(16))  # Outputs: 4.0
```

### 16.2 **Using Aliases**

You can use aliases to shorten module names.

```python
import numpy as np
arr = np.array([1, 2, 3])
print(arr)  # Outputs: [1 2 3]
```

---

## 17. **Regular Expressions**

### 17.1 **Match a Pattern**

You can use the `re` module to work with regular expressions.

```python
import re
pattern = r'\d+'
result = re.findall(pattern, "There are 24 apples and 42 bananas.")
print(result)  # Outputs: ['24', '42']
```

---

## 18. **Iterators and Generators**

### 18.1 **Iterators**

Iterators are objects that can be iterated upon.

```python
my_list = [1, 2, 3]
iterator = iter(my_list)
print(next(iterator))  # Outputs: 1
```

### 18.2 **Generators**

Generators are functions that return an iterable set of items, one at a time, in a special way.

```python
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

gen = count_up_to(3)
print(next(gen))  # Outputs: 1
```

---

## 19. **Object-Oriented Programming (OOP)**

### 19.1 **Defining a Class**

Classes are blueprints for creating objects.

```python
class Dog:
    def __init__(self, name):
        self.name = name
    
    def bark(self):
        return f"{self.name} says woof!"

dog = Dog("Buddy")
print(dog.bark())  # Outputs: Buddy says woof!
```

---

## 20. **Popular Libraries**

### 20.1 **NumPy (for Scientific Computing)**

NumPy is a library for scientific computing with Python.

```python
import numpy as np
arr = np.array([1, 2, 3, 4])
print(arr + 5)  # Outputs: [6 7 8 9]
```

### 20.2 **Pandas (for Data Manipulation)**

Pandas is a library for data manipulation and analysis.

```python
import pandas as pd
data = {'Name': ['Alice', 'Bob'], 'Age': [25, 30]}
df = pd.DataFrame(data)
print(df)
```

---

This Python cheatsheet covers the most commonly used functions and concepts in Python. The sections are designed to provide quick access to useful code snippets and explanations to enhance your Python programming knowledge.