# PostgreSQL Cheatsheet

This cheatsheet is a comprehensive guide to the most important PostgreSQL commands and operations. It covers basic queries, joins, subqueries, indexes, and more advanced concepts.

## Table of Contents

1. [PostgreSQL Basics](#postgresql-basics)
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
12. [Advanced PostgreSQL](#advanced-postgresql)
13. [Best Practices](#best-practices)

---

## PostgreSQL Basics

### Structure of a SQL Query

```sql
SELECT column1, column2
FROM table_name
WHERE condition
ORDER BY column
LIMIT n;
```

### Commenting in SQL

- **Single-line comment**: `-- This is a comment`
- **Multi-line comment**: 
  ```sql
  /* This is a 
     multi-line comment */
  ```

---

## Data Definition Language (DDL)

### Creating a Table

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
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    hire_date DATE
);
```

### Altering a Table

#### Adding a Column

```sql
ALTER TABLE table_name
ADD COLUMN column_name datatype;
```

#### Dropping a Column

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

#### Modifying a Column

```sql
ALTER TABLE table_name
ALTER COLUMN column_name TYPE datatype;
```

#### Renaming a Table

```sql
ALTER TABLE old_table_name
RENAME TO new_table_name;
```

### Dropping a Table

```sql
DROP TABLE table_name;
```

### Creating an Index

```sql
CREATE INDEX index_name
ON table_name (column_name);
```

### Dropping an Index

```sql
DROP INDEX index_name;
```

---

## Data Manipulation Language (DML)

### Inserting Data into a Table

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

Example:

```sql
INSERT INTO employees (name, age, hire_date)
VALUES ('John Doe', 30, '2022-01-01');
```

### Updating Data in a Table

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

### Selecting Data from a Table

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

- `*`: Select all columns
- `%`: Wildcard for zero or more characters (in `LIKE` clause)
- `_`: Wildcard for exactly one character (in `LIKE` clause)

Example:

```sql
SELECT * FROM employees WHERE name LIKE 'J%';
```

---

## Data Control Language (DCL)

### Granting Permissions

```sql
GRANT permission ON object TO user;
```

Example:

```sql
GRANT SELECT, INSERT ON employees TO user1;
```

### Revoking Permissions

```sql
REVOKE permission ON object FROM user;
```

Example:

```sql
REVOKE SELECT ON employees FROM user1;
```

---

## Joins

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

### Subquery in SELECT

```sql
SELECT column1, (SELECT column2 FROM table2 WHERE condition) AS alias
FROM table1;
```

### Subquery in WHERE

```sql
SELECT column1
FROM table1
WHERE column2 IN (SELECT column2 FROM table2 WHERE condition);
```

### Subquery in FROM

```sql
SELECT alias.column1
FROM (SELECT column1 FROM table2 WHERE condition) AS alias;
```

---

## Indexes

### Creating an Index

```sql
CREATE INDEX index_name
ON table_name (column1, column2);
```

### Dropping an Index

```sql
DROP INDEX index_name;
```

### Unique Index

Ensures that all values in a column (or group of columns) are unique.

```sql
CREATE UNIQUE INDEX index_name
ON table_name (column_name);
```

---

## Aggregation Functions

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

### Starting a Transaction

```sql
BEGIN;
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

## Advanced PostgreSQL

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

This PostgreSQL cheatsheet covers all the essential PostgreSQL commands and techniques you’ll need for working with relational databases. Whether you are querying, inserting, updating, or joining data, this guide will help you work more effectively with PostgreSQL.
