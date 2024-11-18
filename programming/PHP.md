# PHP Cheatsheet

A complete reference for PHP, including arrays, objects, file operations, conditionals, loops, MySQL connection, CRUD operations, and more.

---

## Table of Contents

1. [Basic Syntax](#1-basic-syntax)
2. [Variables](#2-variables)
3. [Data Types](#3-data-types)
4. [Form Handling](#4-form-handling)
    1. [Form Handling Example](#41-simple-form)
    2. [Handling Form Submission](#42-handling-form-submission-in-php-post)
    3. [Form Validation](#5-validation)
5. [File Uploading](#6-file-uploading)
6. [MySQL Database Connection](#7-mysql-database-connection)
7. [CRUD Operations](#8-crud-operations)
    1. [Create (Insert)](#81-create-insert-data)
    2. [Read (Select)](#82-read-select-data)
    3. [Update (Modify)](#83-update-data)
    4. [Delete (Remove)](#84-delete-data)
8. [Prepared Statements](#9-prepared-statements)
9. [Error Handling](#10-error-handling)
10. [Sessions](#11-sessions)
11. [Redirecting](#12-redirecting-to-another-page)
12. [Comments](#13-comments)
13. [Constants](#14-constants)
14. [Functions](#15-functions)
15. [Arrays](#16-arrays)
    1. [Indexed Arrays](#161-indexed-arrays)
    2. [Associative Arrays](#162-associative-arrays)
    3. [Multidimensional Arrays](#163-multidimensional-arrays)
    4. [Array Functions](#164-array-functions)
16. [Objects](#17-objects)
    1. [Creating Classes](#171-creating-classes)
    2. [Properties and Methods](#172-properties-and-methods)
    3. [Constructors](#173-constructors)
17. [Conditionals](#18-conditionals)
    1. [If-Else](#181-if-else)
    2. [Switch-Case](#182-switch-case)
18. [Loops](#19-loops)
    1. [For Loop](#191-for-loop)
    2. [While Loop](#192-while-loop)
    3. [Do-While Loop](#193-do-while-loop)
    4. [Foreach Loop](#194-foreach-loop)
19. [File Operations](#20-file-operations)
    1. [Reading a File](#201-reading-a-file)
    2. [Writing to a File](#202-writing-to-a-file)
    3. [File Uploads](#203-file-upload)
    4. [File Deletion](#204-file-deletion)

---

## 1. **Basic Syntax**
```php
<?php
    echo "Hello, World!";
?>
```

---

## 2. **Variables**
```php
$variable_name = "value";  // Assigning a string
$number = 123;             // Assigning an integer
$float_number = 3.14;      // Assigning a float
$boolean = true;           // Assigning a boolean
```

---

## 3. **Data Types**
- String
- Integer
- Float
- Boolean
- Array
- Object
- Null

```php
$name = "John";        // String
$age = 30;             // Integer
$pi = 3.14;            // Float
$is_active = true;     // Boolean
$fruits = array("Apple", "Banana", "Orange");  // Array
```

---

## 4. **Form Handling**

### 4.1 **Simple Form**
```html
<form action="process_form.php" method="POST">
    Name: <input type="text" name="name">
    Age: <input type="number" name="age">
    <input type="submit">
</form>
```

### 4.2 **Handling Form Submission in PHP (POST)**
```php
<?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $name = $_POST['name'];
        $age = $_POST['age'];
        echo "Name: $name, Age: $age";
    }
?>
```

---

## 5. **Validation**

### 5.1 **Basic Form Validation**
```php
<?php
    $name = $age = "";
    $nameErr = $ageErr = "";

    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        if (empty($_POST["name"])) {
            $nameErr = "Name is required";
        } else {
            $name = test_input($_POST["name"]);
        }

        if (empty($_POST["age"])) {
            $ageErr = "Age is required";
        } else {
            $age = test_input($_POST["age"]);
        }
    }

    function test_input($data) {
        return htmlspecialchars(stripslashes(trim($data)));
    }
?>
```

---

## 6. **File Uploading**

### 6.1 **File Upload Form**
```html
<form action="upload.php" method="POST" enctype="multipart/form-data">
    Select image to upload: <input type="file" name="fileToUpload" id="fileToUpload">
    <input type="submit" value="Upload Image" name="submit">
</form>
```

### 6.2 **Handling File Upload in PHP**
```php
<?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $target_dir = "uploads/";
        $target_file = $target_dir . basename($_FILES["fileToUpload"]["name"]);

        if (move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $target_file)) {
            echo "The file ". htmlspecialchars(basename($_FILES["fileToUpload"]["name"])). " has been uploaded.";
        } else {
            echo "Sorry, there was an error uploading your file.";
        }
    }
?>
```

---

## 7. **MySQL Database Connection**

### 7.1 **Using `mysqli` (MySQL Improved)**
```php
<?php
    $servername = "localhost";
    $username = "root";
    $password = "";
    $dbname = "testdb";

    // Create connection
    $conn = new mysqli($servername, $username, $password, $dbname);

    // Check connection
    if ($conn->connect_error) {
        die("Connection failed: " . $conn->connect_error);
    } else {
        echo "Connected successfully";
    }
?>
```

---

## 8. **CRUD Operations**

### 8.1 **Create (Insert Data)**
```php
<?php
    $sql = "INSERT INTO Users (username, email)
            VALUES ('JohnDoe', 'john@example.com')";

    if ($conn->query($sql) === TRUE) {
        echo "New record created successfully";
    } else {
        echo "Error: " . $sql . "<br>" . $conn->error;
    }
?>
```

### 8.2 **Read (Select Data)**
```php
<?php
    $sql = "SELECT id, username, email FROM Users";
    $result = $conn->query($sql);

    if ($result->num_rows > 0) {
        // output data of each row
        while($row = $result->fetch_assoc()) {
            echo "id: " . $row["id"]. " - Name: " . $row["username"]. " - Email: " . $row["email"]. "<br>";
        }
    } else {
        echo "0 results";
    }
?>
```

### 8.3 **Update Data**
```php
<?php
    $sql = "UPDATE Users SET email='newemail@example.com' WHERE username='JohnDoe'";

    if ($conn->query($sql) === TRUE) {
        echo "Record updated successfully";
    } else {
        echo "Error updating record: " . $conn->error;
    }
?>
```

### 8.4 **Delete Data**
```php
<?php
    $sql = "DELETE FROM Users WHERE username='JohnDoe'";

    if ($conn->query($sql) === TRUE) {
        echo "Record deleted successfully";
    } else {
        echo "Error deleting record: " . $conn->error;
    }
?>
```

---

## 9. **Prepared Statements**

### 9.1 **Insert Using Prepared Statements**
```php
<?php
    $stmt = $conn->prepare("INSERT INTO Users (username, email) VALUES (?, ?)");
    $stmt->bind_param("ss", $username, $email);

    // Set parameters and execute
    $username = "JaneDoe";
    $email = "jane@example.com";
    $stmt->execute();

    echo "New record created successfully";

    $stmt->close();
?>
```

---

## 10. **Error Handling**

### 10.1 **Custom Error Handler**
```php
<?php
    function customError($errno, $errstr) {
        echo "Error: [$errno] $errstr";
    }

    set_error_handler("customError");

    echo($test); 

 // This will cause a notice-level error
?>
```

---

## 11. **Sessions**

### 11.1 **Starting a Session**
```php
<?php
    session_start();
    $_SESSION["user"] = "John";
    echo "Session variable is set.";
?>
```

---

## 12. **Redirecting**

### 12.1 **Redirect to Another Page**
```php
<?php
    header("Location: http://example.com");
    exit();
?>
```

---

## 13. **Comments**

### 13.1 **Single-line Comment**
```php
// This is a single-line comment
```

### 13.2 **Multi-line Comment**
```php
/*
This is a multi-line comment
*/
```

---

## 14. **Constants**

### 14.1 **Define a Constant**
```php
define("SITE_NAME", "My Website");
echo SITE_NAME;
```

---

## 15. **Functions**

### 15.1 **Creating a Function**
```php
<?php
    function greet($name) {
        return "Hello, " . $name;
    }

    echo greet("John");
?>
```

---

## 16. **Arrays**

### 16.1 **Indexed Arrays**
```php
$fruits = array("Apple", "Banana", "Cherry");
echo $fruits[0]; // Outputs "Apple"
```

### 16.2 **Associative Arrays**
```php
$person = array("name" => "John", "age" => 30);
echo $person["name"]; // Outputs "John"
```

### 16.3 **Multidimensional Arrays**
```php
$people = array(
    array("name" => "John", "age" => 30),
    array("name" => "Jane", "age" => 28)
);
echo $people[0]["name"]; // Outputs "John"
```

### 16.4 **Array Functions**
```php
$fruits = array("apple", "banana", "cherry");
sort($fruits);  // Sort array
print_r($fruits);  // Prints sorted array
```

---

## 17. **Objects**

### 17.1 **Creating Classes**
```php
class Car {
    public $model;
    public $color;

    function __construct($model, $color) {
        $this->model = $model;
        $this->color = $color;
    }

    function display() {
        echo "Car model: " . $this->model . ", color: " . $this->color;
    }
}

$car1 = new Car("Tesla", "Red");
$car1->display();
```

---

## 18. **Conditionals**

### 18.1 **If-Else**
```php
$age = 20;

if ($age >= 18) {
    echo "Adult";
} else {
    echo "Minor";
}
```

### 18.2 **Switch-Case**
```php
$day = "Monday";

switch ($day) {
    case "Monday":
        echo "Start of the week";
        break;
    case "Friday":
        echo "End of the week";
        break;
    default:
        echo "Middle of the week";
}
```

---

## 19. **Loops**

### 19.1 **For Loop**
```php
for ($i = 0; $i < 5; $i++) {
    echo $i;
}
```

### 19.2 **While Loop**
```php
$i = 0;
while ($i < 5) {
    echo $i;
    $i++;
}
```

### 19.3 **Do-While Loop**
```php
$i = 0;
do {
    echo $i;
    $i++;
} while ($i < 5);
```

### 19.4 **Foreach Loop**
```php
$fruits = array("Apple", "Banana", "Orange");

foreach ($fruits as $fruit) {
    echo $fruit;
}
```

---

## 20. **File Operations**

### 20.1 **Reading a File**
```php
$file = fopen("file.txt", "r");
echo fread($file, filesize("file.txt"));
fclose($file);
```

### 20.2 **Writing to a File**
```php
$file = fopen("file.txt", "w");
fwrite($file, "Hello, World!");
fclose($file);
```

### 20.3 **File Upload**
```php
if (move_uploaded_file($_FILES["file"]["tmp_name"], "uploads/" . $_FILES["file"]["name"])) {
    echo "File is uploaded.";
} else {
    echo "File upload failed.";
}
```

### 20.4 **File Deletion**
```php
if (unlink("file.txt")) {
    echo "File deleted.";
} else {
    echo "File deletion failed.";
}
```

---
