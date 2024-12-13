# SQL Filtering and Sorting Cheatsheet with Real-life Examples

This cheatsheet explains the SQL clauses like `WHERE`, `HAVING`, `ORDER BY`, `GROUP BY`, and other related clauses using real-life examples with the `employees` and `departments` tables.

## Table of Contents

1. [Tables Structure](#tables-structure)
2. [WHERE Clause](#where-clause)
3. [GROUP BY Clause](#group-by-clause)
4. [HAVING Clause](#having-clause)
5. [ORDER BY Clause](#order-by-clause)
6. [LIMIT Clause](#limit-clause)
7. [DISTINCT Clause](#distinct-clause)
8. [AND, OR, NOT Operators](#and-or-not-operators)

---

## Tables Structure

### `employees` Table

| emp_id | name           | age | department_id | hire_date   | salary |
|--------|----------------|-----|---------------|-------------|--------|
| 1      | John Smith     | 35  | 101           | 2020-01-01  | 5000   |
| 2      | Jane Doe       | 28  | 102           | 2019-03-15  | 6000   |
| 3      | Alice Johnson  | 40  | 103           | 2018-06-20  | 7000   |
| 4      | Bob Brown      | 55  | NULL          | 2015-11-10  | 8000   |
| 5      | Charlie Black  | 30  | 102           | 2021-02-01  | 5500   |

### `departments` Table

| dept_id | dept_name     |
|---------|---------------|
| 101     | HR            |
| 102     | IT            |
| 103     | Finance       |
| 104     | Marketing     |

---

## WHERE Clause

The **WHERE** clause is used to filter records based on specified conditions.

### SQL Query

```sql
SELECT name, age, salary
FROM employees
WHERE age > 30;
```

### Result

| name           | age | salary |
|----------------|-----|--------|
| John Smith     | 35  | 5000   |
| Alice Johnson  | 40  | 7000   |
| Bob Brown      | 55  | 8000   |

**Explanation**: The `WHERE` clause filters the rows to include only employees who are older than 30 years.

### Example with `AND` Operator

```sql
SELECT name, age, salary
FROM employees
WHERE age > 30 AND salary > 5000;
```

### Result

| name          | age | salary |
|---------------|-----|--------|
| Alice Johnson | 40  | 7000   |
| Bob Brown     | 55  | 8000   |

**Explanation**: The `WHERE` clause filters employees who are older than 30 and have a salary greater than 5000.

---

## GROUP BY Clause

The **GROUP BY** clause is used to group rows that have the same values into summary rows, like finding the number of employees in each department.

### SQL Query

```sql
SELECT department_id, COUNT(*) AS employee_count
FROM employees
GROUP BY department_id;
```

### Result

| department_id | employee_count |
|---------------|----------------|
| 101           | 1              |
| 102           | 2              |
| 103           | 1              |

**Explanation**: The `GROUP BY` clause groups employees by `department_id` and counts the number of employees in each department.

---

## HAVING Clause

The **HAVING** clause is used to filter groups created by the `GROUP BY` clause. It works like the `WHERE` clause but is used after aggregation.

### SQL Query

```sql
SELECT department_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id
HAVING AVG(salary) > 5500;
```

### Result

| department_id | avg_salary |
|---------------|------------|
| 102           | 5750       |
| 103           | 7000       |

**Explanation**: The `HAVING` clause filters the groups based on the average salary of employees in each department. Only departments with an average salary greater than 5500 are included.

---

## ORDER BY Clause

The **ORDER BY** clause is used to sort the result set by one or more columns. By default, it sorts in ascending order; to sort in descending order, use `DESC`.

### SQL Query (Ascending Order)

```sql
SELECT name, salary
FROM employees
ORDER BY salary;
```

### Result

| name           | salary |
|----------------|--------|
| John Smith     | 5000   |
| Charlie Black  | 5500   |
| Jane Doe       | 6000   |
| Alice Johnson  | 7000   |
| Bob Brown      | 8000   |

**Explanation**: The result is sorted by salary in ascending order.

### SQL Query (Descending Order)

```sql
SELECT name, salary
FROM employees
ORDER BY salary DESC;
```

### Result

| name          | salary |
|---------------|--------|
| Bob Brown     | 8000   |
| Alice Johnson | 7000   |
| Jane Doe      | 6000   |
| Charlie Black | 5500   |
| John Smith    | 5000   |

**Explanation**: The result is sorted by salary in descending order.

---

## LIMIT Clause

The **LIMIT** clause is used to specify the number of records to return from the result set. This is particularly useful for paging or limiting large result sets.

### SQL Query

```sql
SELECT name, salary
FROM employees
ORDER BY salary DESC
LIMIT 3;
```

### Result

| name           | salary |
|----------------|--------|
| Bob Brown      | 8000   |
| Alice Johnson  | 7000   |
| Jane Doe       | 6000   |

**Explanation**: The `LIMIT` clause restricts the output to only the top 3 highest-paid employees.

---

## DISTINCT Clause

The **DISTINCT** clause is used to return only distinct (different) values in a result set, removing duplicates.

### SQL Query

```sql
SELECT DISTINCT department_id
FROM employees;
```

### Result

| department_id |
|---------------|
| 101           |
| 102           |
| 103           |

**Explanation**: The `DISTINCT` clause returns unique `department_id` values, eliminating duplicates.

---

## AND, OR, NOT Operators

The **AND**, **OR**, and **NOT** operators are used to combine multiple conditions in the `WHERE` clause.

### AND Operator

The `AND` operator is used to combine two or more conditions. The result will include only rows where all conditions are true.

```sql
SELECT name, age, salary
FROM employees
WHERE age > 30 AND salary > 5500;
```

### Result

| name          | age | salary |
|---------------|-----|--------|
| Alice Johnson | 40  | 7000   |
| Bob Brown     | 55  | 8000   |

**Explanation**: The `WHERE` clause filters rows where both conditions (`age > 30` and `salary > 5500`) are true.

### OR Operator

The `OR` operator is used when only one of the conditions must be true.

```sql
SELECT name, age, salary
FROM employees
WHERE age < 30 OR salary > 7000;
```

### Result

| name           | age | salary |
|----------------|-----|--------|
| Jane Doe       | 28  | 6000   |
| Alice Johnson  | 40  | 7000   |
| Bob Brown      | 55  | 8000   |

**Explanation**: The `WHERE` clause filters rows where either `age < 30` or `salary > 7000` is true.

### NOT Operator

The `NOT` operator is used to exclude rows where a condition is true.

```sql
SELECT name, age, salary
FROM employees
WHERE NOT salary > 6000;
```

### Result

| name         | age | salary |
|--------------|-----|--------|
| John Smith   | 35  | 5000   |
| Charlie Black| 30  | 5500   |
| Jane Doe     | 28  | 6000   |

**Explanation**: The `WHERE` clause filters rows where `salary > 6000` is false, meaning it returns employees earning 6000 or less.

---

## Conclusion

This cheatsheet explains how to filter, group, and sort data using SQL’s `WHERE`, `HAVING`, `ORDER BY`, `GROUP BY`, and other clauses with real-life examples from the `employees` and `departments` tables. Understanding these clauses is fundamental for writing efficient SQL queries, performing data analysis, and managing databases effectively.
