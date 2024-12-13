# SQL Joins Cheatsheet with Real-life Examples

This cheatsheet explains the different types of SQL joins (INNER, LEFT, RIGHT, FULL OUTER) with real-life examples using two tables: `employees` and `departments`.

## Table of Contents

1. [Tables Structure](#tables-structure)
2. [INNER JOIN](#inner-join)
3. [LEFT JOIN](#left-join)
4. [RIGHT JOIN](#right-join)
5. [FULL OUTER JOIN](#full-outer-join)

---

## Tables Structure

### `employees` Table

| emp_id | name        | department_id |
|--------|-------------|---------------|
| 1      | John Smith  | 101           |
| 2      | Jane Doe    | 102           |
| 3      | Alice Johnson | 103           |
| 4      | Bob Brown   | NULL          |
| 5      | Charlie Black | 102           |

### `departments` Table

| dept_id | dept_name     |
|---------|---------------|
| 101     | HR            |
| 102     | IT            |
| 103     | Finance       |
| 104     | Marketing     |

---

## INNER JOIN

An **INNER JOIN** returns records that have matching values in both tables. If there is no match, the row is excluded.

### SQL Query

```sql
SELECT e.emp_id, e.name, d.dept_name
FROM employees e
INNER JOIN departments d
ON e.department_id = d.dept_id;
```

### Result

| emp_id | name           | dept_name |
|--------|----------------|-----------|
| 1      | John Smith     | HR        |
| 2      | Jane Doe       | IT        |
| 3      | Alice Johnson  | Finance   |
| 5      | Charlie Black  | IT        |

**Explanation**: The `INNER JOIN` only includes employees who are assigned to a department that exists in the `departments` table. Employee `Bob Brown` (emp_id = 4) is excluded because he has no matching `department_id`.

---

## LEFT JOIN (or LEFT OUTER JOIN)

A **LEFT JOIN** returns all records from the left table (here, `employees`), and the matched records from the right table (`departments`). If there is no match, NULL values are returned for columns from the right table.

### SQL Query

```sql
SELECT e.emp_id, e.name, d.dept_name
FROM employees e
LEFT JOIN departments d
ON e.department_id = d.dept_id;
```

### Result

| emp_id | name           | dept_name |
|--------|----------------|-----------|
| 1      | John Smith     | HR        |
| 2      | Jane Doe       | IT        |
| 3      | Alice Johnson  | Finance   |
| 4      | Bob Brown      | NULL      |
| 5      | Charlie Black  | IT        |

**Explanation**: The `LEFT JOIN` includes all employees, even if they do not belong to a department. Employee `Bob Brown` has no department, so `NULL` is returned for `dept_name`.

---

## RIGHT JOIN (or RIGHT OUTER JOIN)

A **RIGHT JOIN** returns all records from the right table (`departments`), and the matched records from the left table (`employees`). If there is no match, NULL values are returned for columns from the left table.

### SQL Query

```sql
SELECT e.emp_id, e.name, d.dept_name
FROM employees e
RIGHT JOIN departments d
ON e.department_id = d.dept_id;
```

### Result

| emp_id | name           | dept_name |
|--------|----------------|-----------|
| 1      | John Smith     | HR        |
| 2      | Jane Doe       | IT        |
| 3      | Alice Johnson  | Finance   |
| NULL   | NULL           | Marketing |

**Explanation**: The `RIGHT JOIN` includes all departments, even if they do not have any employees assigned. The `Marketing` department (dept_id = 104) has no employees, so `NULL` is returned for `emp_id` and `name`.

---

## FULL OUTER JOIN

A **FULL OUTER JOIN** returns all records when there is a match in either the left (`employees`) or the right (`departments`) table. If there is no match, NULL values are returned for columns of the table that does not have a match.

### SQL Query

```sql
SELECT e.emp_id, e.name, d.dept_name
FROM employees e
FULL OUTER JOIN departments d
ON e.department_id = d.dept_id;
```

### Result

| emp_id | name           | dept_name |
|--------|----------------|-----------|
| 1      | John Smith     | HR        |
| 2      | Jane Doe       | IT        |
| 3      | Alice Johnson  | Finance   |
| 4      | Bob Brown      | NULL      |
| 5      | Charlie Black  | IT        |
| NULL   | NULL           | Marketing |

**Explanation**: The `FULL OUTER JOIN` includes all records from both tables. Employee `Bob Brown` appears with a `NULL` in `dept_name`, and the `Marketing` department appears with `NULL` in `emp_id` and `name`.

---

## Summary of Joins

| Join Type          | Description                                               | Output Examples |
|--------------------|-----------------------------------------------------------|-----------------|
| **INNER JOIN**     | Returns only rows with matching values in both tables.    | Employees with matching departments. |
| **LEFT JOIN**      | Returns all rows from the left table and matched rows from the right. Unmatched rows from the right are returned as NULL. | All employees, including those with no department. |
| **RIGHT JOIN**     | Returns all rows from the right table and matched rows from the left. Unmatched rows from the left are returned as NULL. | All departments, including those with no employees. |
| **FULL OUTER JOIN**| Returns all rows when there is a match in either the left or right table. | All employees and departments, including unmatched ones. |

---

## Conclusion

SQL Joins are essential when working with multiple related tables. Understanding how to use different types of joins allows you to retrieve and combine data based on different conditions. The examples above should help you understand how each join type behaves with real-life data scenarios.