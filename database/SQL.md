# SQL Cheatsheet

This cheatsheet is a comprehensive guide to the most important SQL commands and operations. It covers basic queries, joins, subqueries, indexes, and more advanced concepts.

## Table of Contents

1. [SQL Basics](#sql-basics)
2. [Data Definition Language (DDL)](#data-definition-language-ddl)
3. [Data Manipulation Language (DML)](#data-manipulation-language-dml)
4. [Data Query Language (DQL)](#data-query-language-dql)
5. [Data Control Language (DCL)](#data-control-language-dcl)
6. [Joins](#joins)
7. [Subqueries](#subqueries)
8. [Indexes](#indexes)
9. [Aggregation Functions](#aggregation-functions)
10. [Grouping and Sorting](#grouping-and-sorting)
11. [Transactions](#transactions)
12. [Advanced SQL](#advanced-sql)
13. [Best Practices](#best-practices)

---

## SQL Basics

### Structure of a SQL Query

A basic SQL query consists of several clauses such as SELECT, FROM, WHERE, ORDER BY, and LIMIT. These clauses are used to retrieve and manipulate data from a database.

```sql
SELECT column1, column2
FROM table_name
WHERE condition
ORDER BY column
LIMIT n;
```

### Commenting in SQL

Comments are used to explain sections of SQL code. They are ignored by the SQL engine.

- **Single-line comment**: `-- This is a comment`
- **Multi-line comment**: 
  ```sql
  /* This is a 
     multi-line comment */
  ```

---

## Data Definition Language (DDL)

DDL commands are used to define and modify the structure of database objects such as tables, indexes, and constraints.

### Creating a Table

The `CREATE TABLE` statement is used to create a new table in the database.

```sql
CREATE TABLE table_name (
    column1 datatype [constraints],
    column2 datatype [constraints],
    ...
);
```

Example:

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    hire_date DATE
);
```

### Altering a Table

The `ALTER TABLE` statement is used to modify an existing table structure.

#### Adding a Column

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

#### Dropping a Column

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

#### Modifying a Column

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```

#### Renaming a Table

```sql
ALTER TABLE old_table_name
RENAME TO new_table_name;
```

### Dropping a Table

The `DROP TABLE` statement is used to delete a table and its data from the database.

```sql
DROP TABLE table_name;
```

### Creating an Index

Indexes are used to speed up the retrieval of rows by using a pointer.

```sql
CREATE INDEX index_name
ON table_name (column_name);
```

### Dropping an Index

The `DROP INDEX` statement is used to delete an index from the database.

```sql
DROP INDEX index_name;
```

---

## Data Manipulation Language (DML)

DML commands are used to manipulate data stored in the database.

### Inserting Data into a Table

The `INSERT INTO` statement is used to add new rows of data to a table.

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

Example:

```sql
INSERT INTO employees (id, name, age, hire_date)
VALUES (1, 'John Doe', 30, '2022-01-01');
```

### Updating Data in a Table

The `UPDATE` statement is used to modify existing data in a table.

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

Example:

```sql
UPDATE employees
SET age = 31
WHERE id = 1;
```

### Deleting Data from a Table

The `DELETE` statement is used to remove rows from a table.

```sql
DELETE FROM table_name
WHERE condition;
```

Example:

```sql
DELETE FROM employees
WHERE id = 1;
```

---

## Data Query Language (DQL)

DQL commands are used to query the database and retrieve data.

### Selecting Data from a Table

The `SELECT` statement is used to fetch data from a database.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition
ORDER BY column
LIMIT n;
```

Example:

```sql
SELECT * FROM employees;
SELECT name, age FROM employees WHERE age > 30;
```

### Wildcards

Wildcards are used in SQL to search for data within a table.

- `*`: Select all columns
- `%`: Wildcard for zero or more characters (in `LIKE` clause)
- `_`: Wildcard for exactly one character (in `LIKE` clause)

Example:

```sql
SELECT * FROM employees WHERE name LIKE 'J%';
```

---

## Data Control Language (DCL)

DCL commands are used to control access to data in the database.

### Granting Permissions

The `GRANT` statement is used to give users access privileges to the database.

```sql
GRANT permission ON object TO user;
```

Example:

```sql
GRANT SELECT, INSERT ON employees TO 'user1';
```

### Revoking Permissions

The `REVOKE` statement is used to remove access privileges from users.

```sql
REVOKE permission ON object FROM user;
```

Example:

```sql
REVOKE SELECT ON employees FROM 'user1';
```

---

## Joins

Joins are used to combine rows from two or more tables based on a related column between them.

### INNER JOIN

Returns rows when there is a match in both tables.

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### LEFT JOIN (or LEFT OUTER JOIN)

Returns all rows from the left table, and matched rows from the right table. If no match, `NULL` values will appear for columns from the right table.

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

### RIGHT JOIN (or RIGHT OUTER JOIN)

Returns all rows from the right table, and matched rows from the left table. If no match, `NULL` values will appear for columns from the left table.

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

### FULL OUTER JOIN

Returns rows when there is a match in one of the tables.

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

---

## Subqueries

Subqueries are nested queries used to perform operations that require multiple steps.

### Subquery in SELECT

A subquery can be used in the SELECT clause to return a value that will be used in the main query.

```sql
SELECT column1, (SELECT column2 FROM table2 WHERE condition) AS alias
FROM table1;
```

### Subquery in WHERE

A subquery can be used in the WHERE clause to filter the results of the main query.

```sql
SELECT column1
FROM table1
WHERE column2 IN (SELECT column2 FROM table2 WHERE condition);
```

### Subquery in FROM

A subquery can be used in the FROM clause to create a temporary table that will be used in the main query.

```sql
SELECT alias.column1
FROM (SELECT column1 FROM table2 WHERE condition) AS alias;
```

---

## Indexes

Indexes are used to improve the speed of data retrieval operations on a database table.

### Creating an Index

The `CREATE INDEX` statement is used to create an index on one or more columns of a table.

```sql
CREATE INDEX index_name
ON table_name (column1, column2);
```

### Dropping an Index

The `DROP INDEX` statement is used to delete an index from the database.

```sql
DROP INDEX index_name;
```

### Unique Index

A unique index ensures that all values in a column (or group of columns) are unique.

```sql
CREATE UNIQUE INDEX index_name
ON table_name (column_name);
```

---

## Aggregation Functions

Aggregation functions perform a calculation on a set of values and return a single value.

### COUNT

Counts the number of rows that match a specific condition.

```sql
SELECT COUNT(*) FROM table_name WHERE condition;
```

### SUM

Returns the sum of values in a column.

```sql
SELECT SUM(column_name) FROM table_name;
```

### AVG

Returns the average of values in a column.

```sql
SELECT AVG(column_name) FROM table_name;
```

### MIN and MAX

Returns the minimum and maximum values in a column.

```sql
SELECT MIN(column_name), MAX(column_name) FROM table_name;
```

---

## Grouping and Sorting

Grouping and sorting are used to organize and order the result set of a query.

### GROUP BY

Groups rows that have the same values into summary rows.

```sql
SELECT column1, COUNT(*)
FROM table_name
GROUP BY column1;
```

### HAVING

Filters groups after applying `GROUP BY`.

```sql
SELECT column1, COUNT(*)
FROM table_name
GROUP BY column1
HAVING COUNT(*) > 5;
```

### ORDER BY

Sorts the result set in ascending or descending order.

```sql
SELECT column1, column2
FROM table_name
ORDER BY column1 DESC;
```

---

## Transactions

Transactions are used to ensure the integrity of data by grouping multiple operations into a single unit of work.

### Starting a Transaction

```sql
BEGIN TRANSACTION;
```

### Committing a Transaction

```sql
COMMIT;
```

### Rolling Back a Transaction

```sql
ROLLBACK;
```

---

## Advanced SQL

Advanced SQL techniques provide more complex and powerful ways to manipulate and retrieve data.

### CASE WHEN

Conditional logic inside a query.

```sql
SELECT column1,
       CASE
           WHEN condition THEN 'Result 1'
           WHEN condition THEN 'Result 2'
           ELSE 'Default'
       END AS alias
FROM table_name;
```

### UNION and UNION ALL

- **UNION**: Combines the result sets of two or more queries (removes duplicates).
- **UNION ALL**: Combines result sets (keeps duplicates).

```sql
SELECT column FROM table1
UNION
SELECT column FROM table2;

SELECT column FROM table1
UNION ALL
SELECT column FROM table2;
```

---

## Best Practices

- **Use `JOIN` instead of subqueries** when possible for better performance.
- **Index frequently searched columns** to speed up queries.
- **Avoid `SELECT *`** and specify only the columns you need.
- **Use `LIMIT` for large result sets** to restrict the number of rows returned.
- **Normalize your data** to avoid redundancy and improve consistency.
- **Use `WHERE` clauses** instead of `HAVING` to filter data before aggregation.
- **Test queries** for performance, especially for large datasets.
- **Use transactions** to ensure data consistency, especially for operations that involve multiple DML statements.

---

## Conclusion

This SQL cheatsheet covers all the essential SQL commands and techniques you’ll need for working with relational databases. Whether you are querying, inserting, updating, or joining data, this guide will help you work more effectively with SQL.
