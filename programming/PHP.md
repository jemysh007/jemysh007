# PHP Cheatsheet

This is a comprehensive PHP cheatsheet, covering everything from basic syntax and operations to advanced topics like MySQL interaction, file handling, and more. This guide is perfect for both beginners and experienced developers.

---

## Table of Contents

1. [Basic Syntax](#1-basic-syntax)
2. [Constants](#2-constants)
3. [Data Types](#3-data-types)
4. [Comments](#4-comments)
5. [Variables](#5-variables)
6. [Arrays](#6-arrays)
7. [Conditionals](#7-conditionals)
8. [Loops](#8-loops)
9. [Functions](#9-functions)
10. [Objects](#10-objects)
11. [File Operations](#11-file-operations)
12. [MySQL Database Operations](#12-mysql-database-operations)
    - 12.1 [MySQL Connection](#121-mysql-connection)
    - 12.2 [CRUD Operations](#122-crud-operations)
    - 12.3 [Prepared Statements](#123-prepared-statements)
13. [File Uploads & Validation](#13-file-uploads--validation)
14. [Sessions](#14-sessions)
15. [Redirecting to Another Page](#15-redirecting-to-another-page)
16. [Superglobals](#16-superglobals)
17. [Error Handling](#17-error-handling)
18. [Date and Time](#18-date-and-time)
19. [Security](#19-security)
20. [Useful Functions](#20-useful-functions)

---

## 1. **Basic Syntax**

PHP code is written inside `<?php ?>` tags. Below is the syntax:

```php
<?php
echo "Hello, World!";
?>
```
- **Explanation**: PHP scripts are embedded in HTML or can be run standalone. `echo` is used to print output to the screen.

---

## 2. **Constants**

```php
define("SITE_NAME", "MyWebsite");
echo SITE_NAME;
```
- **Explanation**: Constants are globally available and cannot be changed once defined. They are case-sensitive by default.

---

## 3. **Data Types**

PHP supports the following data types:
- Integer
- String
- Boolean
- Float (double)
- Array
- Object
- NULL

Example:

```php
$intVar = 5;
$stringVar = "Hello, World!";
$floatVar = 5.7;
$boolVar = true;
```

---

## 4. **Comments**

```php
// This is a single-line comment

/*
This is a multi-line comment
spanning multiple lines
*/
```
- **Explanation**: Comments are used for documentation and to disable code temporarily.

---

## 5. **Variables**

Variables in PHP start with a dollar sign (`$`):

```php
$name = "John";
$age = 25;
```
- **Explanation**: Variables are case-sensitive and can hold any data type.

---

## 6. **Arrays**

### 6.1 **Indexed Array**

```php
$fruits = ["Apple", "Banana", "Orange"];
echo $fruits[0]; // Outputs "Apple"
```

### 6.2 **Associative Array**

```php
$person = [
    "name" => "John",
    "age" => 25
];
echo $person["name"]; // Outputs "John"
```

### 6.3 **Multidimensional Array**

```php
$contacts = [
    ["name" => "John", "email" => "john@example.com"],
    ["name" => "Jane", "email" => "jane@example.com"]
];
echo $contacts[0]["name"]; // Outputs "John"
```

---

## 7. **Conditionals**

### 7.1 **If-Else**

```php
$age = 20;
if ($age >= 18) {
    echo "You are eligible to vote.";
} else {
    echo "You are not eligible to vote.";
}
```
- **Explanation**: `if-else` statements evaluate a condition and execute code based on the result.

### 7.2 **Switch-Case**

```php
$day = "Monday";
switch ($day) {
    case "Monday":
        echo "Start of the week!";
        break;
    case "Friday":
        echo "Almost weekend!";
        break;
    default:
        echo "Have a great day!";
}
```
- **Explanation**: `switch-case` allows you to check multiple values for a single variable.

---

## 8. **Loops**

### 8.1 **For Loop**

```php
for ($i = 0; $i < 5; $i++) {
    echo "Iteration: $i<br>";
}
```
- **Explanation**: A `for` loop runs for a specific number of iterations.

### 8.2 **While Loop**

```php
$i = 0;
while ($i < 5) {
    echo "Iteration: $i<br>";
    $i++;
}
```
- **Explanation**: A `while` loop continues as long as a condition is `true`.

### 8.3 **Do-While Loop**

```php
$i = 0;
do {
    echo "Iteration: $i<br>";
    $i++;
} while ($i < 5);
```
- **Explanation**: A `do-while` loop runs at least once before checking the condition.

### 8.4 **Foreach Loop**

```php
$fruits = ["Apple", "Banana", "Orange"];
foreach ($fruits as $fruit) {
    echo $fruit . "<br>";
}
```
- **Explanation**: `foreach` is used to iterate through arrays.

---

## 9. **Functions**

### 9.1 **Creating a Function**

```php
function greet($name) {
    echo "Hello, $name!";
}
greet("John");
```
- **Explanation**: Functions allow you to reuse code. You can pass parameters and return values.

---

## 10. **Objects**

### 10.1 **Creating Classes**

```php
class Car {
    public $color;
    public $model;

    function __construct($color, $model) {
        $this->color = $color;
        $this->model = $model;
    }

    function display() {
        echo "This car is a $this->color $this->model.";
    }
}
$car = new Car("Red", "Toyota");
$car->display();
```
- **Explanation**: Objects are instances of classes, and they can have properties and methods.

---

## 11. **File Operations**

### 11.1 **Reading a File**

```php
$file = fopen("example.txt", "r");
echo fread($file, filesize("example.txt"));
fclose($file);
```

### 11.2 **Writing to a File**

```php
$file = fopen("example.txt", "w");
fwrite($file, "Hello, World!");
fclose($file);
```

### 11.3 **File Deletion**

```php
if (unlink("example.txt")) {
    echo "File deleted successfully.";
} else {
    echo "Error deleting file.";
}
```

---

## 12. **MySQL Database Operations**

### 12.1 **MySQL Connection**

```php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "test_db";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
echo "Connected successfully";
```
- **Explanation**: This establishes a connection to the MySQL database using MySQLi.

### 12.2 **CRUD Operations**

#### 12.2.1 **Create (Insert) Data**

```php
$sql = "INSERT INTO users (username, email) VALUES ('JohnDoe', 'john@example.com')";
if ($conn->query($sql) === TRUE) {
    echo "New record created successfully";
} else {
    echo "Error: " . $sql . "<br>" . $conn->error;
}
```

#### 12.2.2 **Read (Select) Data**

```php
$sql = "SELECT id, username, email FROM users";
$result = $conn->query($sql);

if ($result->num_rows > 0) {
    while ($row = $result->fetch_assoc()) {
        echo "id: " . $row["id"]. " - Name: " . $row["username"]. " - Email: " . $row["email"]. "<br>";
    }
} else {
    echo "0 results";
}
```

#### 12.2.3 **Update Data**

```php
$sql = "UPDATE users SET email='newemail@example.com' WHERE username='JohnDoe'";
if ($conn->query($sql) === TRUE) {
    echo "Record updated successfully";
} else {
    echo "Error updating record: " . $conn->error;
}
```

#### 12.2.4 **Delete Data**

```php
$sql = "DELETE FROM users WHERE username='JohnDoe'";
if ($conn->query($sql) === TRUE) {
    echo "Record deleted successfully";
} else {
    echo "Error deleting record: " . $conn->error;
}
```

### 12.3 **Prepared Statements**

```php
$stmt = $conn->

prepare("SELECT id, username, email FROM users WHERE username = ?");
$stmt->bind_param("s", $username);

$username = "JohnDoe";
$stmt->execute();
$stmt->bind_result($id, $username, $email);
while ($stmt->fetch()) {
    echo "id: $id - Name: $username - Email: $email<br>";
}
$stmt->close();
```
- **Explanation**: Prepared statements prevent SQL injection by binding parameters and executing safely.

---

## 13. **File Uploads & Validation**

### 13.1 **File Upload with Validation**

```php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $targetDir = "uploads/";
    $targetFile = $targetDir . basename($_FILES["fileToUpload"]["name"]);
    $uploadOk = 1;
    $imageFileType = strtolower(pathinfo($targetFile, PATHINFO_EXTENSION));

    if (isset($_POST["submit"])) {
        $check = getimagesize($_FILES["fileToUpload"]["tmp_name"]);
        if ($check !== false) {
            $uploadOk = 1;
        } else {
            $uploadOk = 0;
        }
    }

    if ($_FILES["fileToUpload"]["size"] > 5000000) {
        $uploadOk = 0;
    }

    if ($imageFileType != "jpg" && $imageFileType != "png" && $imageFileType != "jpeg" && $imageFileType != "gif") {
        $uploadOk = 0;
    }

    if ($uploadOk == 0) {
        echo "Sorry, your file was not uploaded.";
    } else {
        if (move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $targetFile)) {
            echo "The file " . htmlspecialchars(basename($_FILES["fileToUpload"]["name"])) . " has been uploaded.";
        } else {
            echo "Sorry, there was an error uploading your file.";
        }
    }
}
```

### 13.2 **HTML Form for File Upload**

```html
<form action="upload.php" method="post" enctype="multipart/form-data">
    Select image to upload:
    <input type="file" name="fileToUpload" id="fileToUpload">
    <input type="submit" value="Upload Image" name="submit">
</form>
```

---

## 14. **Sessions**

```php
session_start();
$_SESSION["username"] = "JohnDoe";
echo $_SESSION["username"];
```
- **Explanation**: Sessions are used to store data across multiple pages.

---

## 15. **Redirecting to Another Page**

```php
header("Location: https://www.example.com");
exit;
```
- **Explanation**: `header()` is used to redirect users to another page.

---

## 16. **Superglobals**

Superglobals are built-in global arrays in PHP, such as `$_POST`, `$_GET`, `$_SESSION`, `$_FILES`, and `$_SERVER`.

---

## 17. **Error Handling**

```php
try {
    $conn = new mysqli($servername, $username, $password, $dbname);
    if ($conn->connect_error) {
        throw new Exception("Connection failed: " . $conn->connect_error);
    }
} catch (Exception $e) {
    echo "Error: " . $e->getMessage();
}
```

---

## 18. **Date and Time**

```php
echo date("Y-m-d H:i:s");
```

---

## 19. **Security**

- Always use **Prepared Statements** for MySQL to prevent SQL Injection.
- Validate and sanitize **user input** before processing.
- Use **password_hash** and **password_verify** for secure password storage.

---

## 20. **Useful Functions**

Here are **30 useful PHP functions** across different categories, including strings, numbers, arrays, objects, and JSON:

### 1. **`strlen()`**  
Returns the length of a string.
```php
echo strlen("Hello, World!"); // Outputs: 13
```

### 2. **`strpos()`**  
Finds the position of the first occurrence of a substring in a string.
```php
echo strpos("Hello, World!", "World"); // Outputs: 7
```

### 3. **`str_replace()`**  
Replaces all occurrences of the search string with the replacement string.
```php
echo str_replace("World", "PHP", "Hello, World!"); // Outputs: Hello, PHP!
```

### 4. **`substr()`**  
Extracts a substring from a string.
```php
echo substr("Hello, World!", 7, 5); // Outputs: World
```

### 5. **`trim()`**  
Removes whitespace (or other characters) from the beginning and end of a string.
```php
echo trim("  Hello, World!  "); // Outputs: Hello, World!
```

### 6. **`strtoupper()`**  
Converts a string to uppercase.
```php
echo strtoupper("Hello, World!"); // Outputs: HELLO, WORLD!
```

### 7. **`strtolower()`**  
Converts a string to lowercase.
```php
echo strtolower("Hello, World!"); // Outputs: hello, world!
```

### 8. **`ucwords()`**  
Capitalizes the first letter of each word in a string.
```php
echo ucwords("hello, world!"); // Outputs: Hello, World!
```

### 9. **`implode()`**  
Joins array elements into a single string.
```php
$arr = ["PHP", "is", "awesome"];
echo implode(" ", $arr); // Outputs: PHP is awesome
```

### 10. **`explode()`**  
Splits a string into an array based on a delimiter.
```php
$str = "apple,banana,cherry";
$arr = explode(",", $str);
print_r($arr); // Outputs: Array ( [0] => apple [1] => banana [2] => cherry )
```

### 11. **`array_push()`**  
Adds one or more elements to the end of an array.
```php
$arr = [1, 2, 3];
array_push($arr, 4, 5);
print_r($arr); // Outputs: Array ( [0] => 1 [1] => 2 [2] => 3 [3] => 4 [4] => 5 )
```

### 12. **`array_pop()`**  
Removes the last element from an array.
```php
$arr = [1, 2, 3, 4];
array_pop($arr);
print_r($arr); // Outputs: Array ( [0] => 1 [1] => 2 [2] => 3 )
```

### 13. **`array_shift()`**  
Removes the first element from an array.
```php
$arr = [1, 2, 3, 4];
array_shift($arr);
print_r($arr); // Outputs: Array ( [0] => 2 [1] => 3 [2] => 4 )
```

### 14. **`array_unshift()`**  
Adds one or more elements to the beginning of an array.
```php
$arr = [2, 3, 4];
array_unshift($arr, 1);
print_r($arr); // Outputs: Array ( [0] => 1 [1] => 2 [2] => 3 [3] => 4 )
```

### 15. **`count()`**  
Counts all elements in an array.
```php
$arr = [1, 2, 3, 4];
echo count($arr); // Outputs: 4
```

### 16. **`array_merge()`**  
Merges two or more arrays.
```php
$arr1 = [1, 2];
$arr2 = [3, 4];
$result = array_merge($arr1, $arr2);
print_r($result); // Outputs: Array ( [0] => 1 [1] => 2 [2] => 3 [3] => 4 )
```

### 17. **`array_diff()`**  
Compares arrays and returns the difference.
```php
$arr1 = [1, 2, 3];
$arr2 = [2, 3, 4];
$result = array_diff($arr1, $arr2);
print_r($result); // Outputs: Array ( [0] => 1 )
```

### 18. **`json_encode()`**  
Encodes a PHP variable into a JSON string.
```php
$data = ["name" => "John", "age" => 30];
echo json_encode($data); // Outputs: {"name":"John","age":30}
```

### 19. **`json_decode()`**  
Decodes a JSON string into a PHP variable.
```php
$json = '{"name":"John","age":30}';
$obj = json_decode($json);
echo $obj->name; // Outputs: John
```

### 20. **`is_array()`**  
Checks if a variable is an array.
```php
$arr = [1, 2, 3];
echo is_array($arr) ? "Yes" : "No"; // Outputs: Yes
```

### 21. **`is_numeric()`**  
Checks if a value is a number or numeric string.
```php
$var = "123";
echo is_numeric($var) ? "Yes" : "No"; // Outputs: Yes
```

### 22. **`round()`**  
Rounds a floating point number to a specified precision.
```php
echo round(3.14159, 2); // Outputs: 3.14
```

### 23. **`rand()`**  
Generates a random integer.
```php
echo rand(1, 100); // Outputs a random number between 1 and 100
```

### 24. **`number_format()`**  
Formats a number with grouped thousands.
```php
echo number_format(1234567.891, 2); // Outputs: 1,234,567.89
```

### 25. **`isset()`**  
Checks if a variable is set and is not `NULL`.
```php
$var = "Hello";
echo isset($var) ? "Set" : "Not set"; // Outputs: Set
```

### 26. **`empty()`**  
Checks if a variable is empty.
```php
$var = "";
echo empty($var) ? "Empty" : "Not Empty"; // Outputs: Empty
```

### 27. **`array_key_exists()`**  
Checks if a key exists in an array.
```php
$arr = ["name" => "John", "age" => 30];
echo array_key_exists("name", $arr) ? "Exists" : "Doesn't Exist"; // Outputs: Exists
```

### 28. **`date()`**  
Formats a local date and time.
```php
echo date("Y-m-d H:i:s"); // Outputs: 2024-11-18 12:45:00
```

### 29. **`strtotime()`**  
Converts an English textual datetime description into a Unix timestamp.
```php
echo strtotime("next Monday"); // Outputs the timestamp for the next Monday
```

### 30. **`filter_var()`**  
Filters a variable with a specified filter.
```php
$email = "john@example.com";
if (filter_var($email, FILTER_VALIDATE_EMAIL)) {
    echo "Valid email"; // Outputs: Valid email
} else {
    echo "Invalid email";
}
```
---

This documentation provides a broad overview of PHP basics, from syntax to advanced topics. It includes practical examples for each concept, making it easy to implement in your projects.
