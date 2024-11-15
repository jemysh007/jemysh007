# JavaScript Cheat Sheet

This cheat sheet provides a quick reference to common JavaScript syntax, functions, operators, and methods.

---

## 1. **JavaScript Syntax**

### Declaring Variables

```javascript
let variableName = value;  // Block-scoped variable (can be reassigned)
const constantName = value;  // Block-scoped variable (cannot be reassigned)
var oldVariableName = value;  // Function-scoped variable (use let/const instead)
```

---

## 2. **Data Types**

### Primitive Types

- **String**

```javascript
let name = "John";
```

- **Number**

```javascript
let age = 25;
```

- **Boolean**

```javascript
let isActive = true;
```

- **Null**

```javascript
let emptyValue = null;
```

- **Undefined**

```javascript
let notAssigned;
```

- **Symbol (ES6)**

```javascript
let uniqueSymbol = Symbol("unique");
```

- **BigInt (ES11)**

```javascript
let bigNumber = 1234567890123456789012345678901234567890n;
```

### Non-Primitive Type (Object)

```javascript
let person = { name: "John", age: 25 };
```

---

## 3. **Operators**

### Arithmetic Operators

```javascript
let sum = 10 + 5;   // Addition
let difference = 10 - 5;  // Subtraction
let product = 10 * 5;   // Multiplication
let quotient = 10 / 5;   // Division
let remainder = 10 % 3;  // Modulo
let exponent = 10 ** 2;  // Exponentiation
```

### Comparison Operators

```javascript
let isEqual = (10 == 10);   // Loose equality
let isStrictEqual = (10 === 10);  // Strict equality
let isNotEqual = (10 != 5);   // Loose inequality
let isStrictNotEqual = (10 !== 5);  // Strict inequality
let isGreater = (10 > 5);   // Greater than
let isGreaterOrEqual = (10 >= 5);  // Greater than or equal
let isLess = (10 < 5);   // Less than
let isLessOrEqual = (10 <= 5);  // Less than or equal
```

### Logical Operators

```javascript
let and = true && false;  // AND
let or = true || false;  // OR
let not = !true;  // NOT
```

---

## 4. **Control Structures**

### If-Else Statement

```javascript
if (condition) {
    // code to be executed if condition is true
} else {
    // code to be executed if condition is false
}
```

### Switch Statement

```javascript
switch (expression) {
    case value1:
        // code to be executed if expression === value1
        break;
    case value2:
        // code to be executed if expression === value2
        break;
    default:
        // code to be executed if no case matches
}
```

---

## 5. **Functions**

### Function Declaration

```javascript
function greet(name) {
    return "Hello, " + name;
}
```

### Function Expression

```javascript
const greet = function(name) {
    return "Hello, " + name;
};
```

### Arrow Functions (ES6)

```javascript
const greet = (name) => {
    return "Hello, " + name;
};
```

### Implicit Return (One-line arrow function)

```javascript
const greet = (name) => "Hello, " + name;
```

---

## 6. **Arrays**

### Creating an Array

```javascript
let fruits = ["apple", "banana", "cherry"];
```

### Accessing Array Elements

```javascript
let firstFruit = fruits[0];  // "apple"
```

### Array Methods

- **push()** - Adds an element to the end

```javascript
fruits.push("orange");
```

- **pop()** - Removes the last element

```javascript
fruits.pop();
```

- **shift()** - Removes the first element

```javascript
fruits.shift();
```

- **unshift()** - Adds an element to the beginning

```javascript
fruits.unshift("grapes");
```

- **forEach()** - Iterates over the array

```javascript
fruits.forEach((fruit) => console.log(fruit));
```

- **map()** - Creates a new array with the results of a function

```javascript
let uppercasedFruits = fruits.map(fruit => fruit.toUpperCase());
```

- **filter()** - Creates a new array with elements that satisfy a condition

```javascript
let longFruits = fruits.filter(fruit => fruit.length > 5);
```

---

## 7. **Objects**

### Creating an Object

```javascript
let person = { 
    name: "John", 
    age: 25,
    greet: function() {
        return "Hello, " + this.name;
    }
};
```

### Accessing Object Properties

```javascript
let personName = person.name;  // "John"
let personAge = person["age"];  // 25
```

---

## 8. **Loops**

### For Loop

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

### While Loop

```javascript
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}
```

### Do-While Loop

```javascript
let i = 0;
do {
    console.log(i);
    i++;
} while (i < 5);
```

### For...of Loop (for arrays/iterables)

```javascript
for (let fruit of fruits) {
    console.log(fruit);
}
```

### For...in Loop (for objects)

```javascript
for (let key in person) {
    console.log(key + ": " + person[key]);
}
```

---

## 9. **Events**

### Adding Event Listeners

```javascript
let button = document.querySelector("button");
button.addEventListener("click", () => {
    alert("Button clicked!");
});
```

### Removing Event Listeners

```javascript
button.removeEventListener("click", handler);
```

---

## 10. **ES6 Features**

### Destructuring Assignment

- **Array Destructuring**

```javascript
let [first, second] = ["apple", "banana"];
```

- **Object Destructuring**

```javascript
let {name, age} = person;
```

### Template Literals

```javascript
let greeting = `Hello, ${person.name}!`;
```

### Spread Operator

```javascript
let newFruits = [...fruits, "orange"];
```

### Rest Operator

```javascript
function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0);
}
```

---

## 11. **Promises and Async/Await**

### Promises

```javascript
let promise = new Promise((resolve, reject) => {
    let success = true;
    if (success) {
        resolve("Success!");
    } else {
        reject("Failure!");
    }
});

promise.then((message) => {
    console.log(message);
}).catch((message) => {
    console.log(message);
});
```

### Async/Await

```javascript
async function fetchData() {
    let response = await fetch('https://api.example.com/data');
    let data = await response.json();
    console.log(data);
}

fetchData();
```

---

## 12. **Error Handling**

### Try-Catch Block

```javascript
try {
    let result = riskyFunction();
} catch (error) {
    console.error("An error occurred:", error);
} finally {
    console.log("This will run regardless of success or failure");
}
```

---

## Conclusion

This JavaScript cheat sheet summarizes key concepts, methods, and syntax for writing clean, effective code. Keep this as a quick reference while you're coding!