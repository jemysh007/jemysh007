# PHP MySQL Documentation (Object-Oriented MySQL)

This documentation demonstrates how to interact with a MySQL database using **object-oriented** PHP methods for database interactions. The examples will cover creating a database, selecting data, inserting, updating, and deleting data using the `mysqli` extension with object-oriented code.

---

## Table of Contents

1. **Connecting to the Database**
2. **Creating a Database**
3. **Selecting a Database**
4. **Creating a Table**
5. **Inserting Data**
6. **Selecting Data**
7. **Updating Data**
8. **Deleting Data**
9. **Closing the Database Connection**
10. **Error Handling**
11. **Dropping a Database**

---

## 1. **Connecting to the Database**

To connect to a MySQL database using object-oriented `mysqli`:

```php
<?php
$servername = "localhost";
$username = "root";
$password = "";

// Create connection using OOP
$conn = new mysqli($servername, $username, $password);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
echo "Connected successfully";
?>
```

---

## 2. **Creating a Database**

To create a database using the object-oriented `mysqli`:

```php
<?php
$sql = "CREATE DATABASE test_db";
if ($conn->query($sql) === TRUE) {
    echo "Database created successfully";
} else {
    echo "Error creating database: " . $conn->error;
}
?>
```

---

## 3. **Selecting a Database**

Once a database is created, select it for use:

```php
<?php
$conn->select_db("test_db");
?>
```

---

## 4. **Creating a Table**

To create a table within the selected database:

```php
<?php
$sql = "CREATE TABLE users (
    id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(30) NOT NULL,
    email VARCHAR(50),
    reg_date TIMESTAMP
)";

if ($conn->query($sql) === TRUE) {
    echo "Table users created successfully";
} else {
    echo "Error creating table: " . $conn->error;
}
?>
```

---

## 5. **Inserting Data**

To insert data into a table using object-oriented `mysqli`:

```php
<?php
$sql = "INSERT INTO users (name, email)
VALUES ('John Doe', 'john@example.com')";

if ($conn->query($sql) === TRUE) {
    echo "New record created successfully";
} else {
    echo "Error: " . $sql . "<br>" . $conn->error;
}
?>
```

You can also use prepared statements for security and to prevent SQL injection.

### Using Prepared Statements for Insert

```php
<?php
$stmt = $conn->prepare("INSERT INTO users (name, email) VALUES (?, ?)");
$stmt->bind_param("ss", $name, $email);

$name = "Jane Doe";
$email = "jane@example.com";
$stmt->execute();

echo "New record created successfully";
$stmt->close();
?>
```

---

## 6. **Selecting Data**

To select data from a table, you can use object-oriented methods such as `query()` and `fetch_assoc()`.

### Selecting All Rows

```php
<?php
$sql = "SELECT id, name, email FROM users";
$result = $conn->query($sql);

if ($result->num_rows > 0) {
    while($row = $result->fetch_assoc()) {
        echo "id: " . $row["id"]. " - Name: " . $row["name"]. " - Email: " . $row["email"]. "<br>";
    }
} else {
    echo "0 results";
}
?>
```

### Selecting a Single Row

```php
<?php
$sql = "SELECT id, name, email FROM users WHERE id = 1";
$result = $conn->query($sql);

if ($result->num_rows == 1) {
    $row = $result->fetch_assoc();
    echo "id: " . $row["id"]. " - Name: " . $row["name"]. " - Email: " . $row["email"];
} else {
    echo "No results";
}
?>
```

### Using Prepared Statements for Selecting Data

```php
<?php
$stmt = $conn->prepare("SELECT id, name, email FROM users WHERE id = ?");
$stmt->bind_param("i", $id);

$id = 1;
$stmt->execute();
$stmt->bind_result($id, $name, $email);

while ($stmt->fetch()) {
    echo "id: $id - Name: $name - Email: $email";
}

$stmt->close();
?>
```

---

## 7. **Updating Data**

To update existing data, use the `UPDATE` SQL statement with object-oriented `mysqli`.

### Update a Single Record

```php
<?php
$sql = "UPDATE users SET name='John Updated' WHERE id=1";

if ($conn->query($sql) === TRUE) {
    echo "Record updated successfully";
} else {
    echo "Error updating record: " . $conn->error;
}
?>
```

### Using Prepared Statements for Update

```php
<?php
$stmt = $conn->prepare("UPDATE users SET name = ? WHERE id = ?");
$stmt->bind_param("si", $name, $id);

$name = "John Updated";
$id = 1;
$stmt->execute();

echo "Record updated successfully";
$stmt->close();
?>
```

---

## 8. **Deleting Data**

To delete data from a table using object-oriented `mysqli`:

### Delete a Single Record

```php
<?php
$sql = "DELETE FROM users WHERE id=1";

if ($conn->query($sql) === TRUE) {
    echo "Record deleted successfully";
} else {
    echo "Error deleting record: " . $conn->error;
}
?>
```

### Using Prepared Statements for Delete

```php
<?php
$stmt = $conn->prepare("DELETE FROM users WHERE id = ?");
$stmt->bind_param("i", $id);

$id = 1;
$stmt->execute();

echo "Record deleted successfully";
$stmt->close();
?>
```

---

## 9. **Closing the Database Connection**

After performing your database operations, it’s good practice to close the connection.

```php
<?php
$conn->close();
?>
```

---

## 10. **Error Handling**

Error handling can be done using `mysqli_error()` or `mysqli->error` in object-oriented PHP.

### Example: Error Handling

```php
<?php
// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Example of error handling in a query
$sql = "SELECT * FROM non_existing_table";
$result = $conn->query($sql);

if (!$result) {
    echo "Error: " . $conn->error;
}
?>
```

---

## 11. **Dropping a Database**

To drop (delete) a database:

```php
<?php
$sql = "DROP DATABASE test_db";
if ($conn->query($sql) === TRUE) {
    echo "Database dropped successfully";
} else {
    echo "Error dropping database: " . $conn->error;
}
?>
```

---

## Conclusion

This documentation provides a complete guide for interacting with a MySQL database using **object-oriented methods** in PHP. You can perform all basic database operations like creating a database, inserting, selecting, updating, and deleting data, while using object-oriented practices for handling MySQL queries.

This approach improves code readability, security, and maintainability while leveraging the full power of the `mysqli` extension's object-oriented features.