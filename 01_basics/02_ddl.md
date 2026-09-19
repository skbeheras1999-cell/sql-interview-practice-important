# DDL – Data Definition Language

DDL stands for **Data Definition Language**.

DDL commands are used to **create, modify, and remove the structure of database objects** such as tables.

## Main DDL Commands

The commonly used DDL commands are:

* CREATE
* ALTER
* DROP
* TRUNCATE

---

# 1. CREATE

`CREATE` is used to create a new database object such as a table.

## Example

```sql
CREATE TABLE employees (
    employee_id INT,
    employee_name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10,2),
    joining_date DATE
);
```

### Explanation

This creates a table called `employees` with five columns:

| Column        | Data Type     | Description     |
| ------------- | ------------- | --------------- |
| employee_id   | INT           | Employee ID     |
| employee_name | VARCHAR(100)  | Employee name   |
| department    | VARCHAR(50)   | Department name |
| salary        | DECIMAL(10,2) | Employee salary |
| joining_date  | DATE          | Joining date    |

## Insert sample data

```sql
INSERT INTO employees
(employee_id, employee_name, department, salary, joining_date)
VALUES
(101, 'Rahul', 'IT', 55000.00, '2024-01-15'),
(102, 'Priya', 'HR', 48000.00, '2024-02-10'),
(103, 'Amit', 'Finance', 62000.00, '2024-03-20');
```

## Check the table

```sql
SELECT * FROM employees;
```

---

# 2. ALTER

`ALTER` is used to **modify the structure of an existing table**.

For example, we can add a new column.

## Add a column

```sql
ALTER TABLE employees
ADD email VARCHAR(100);
```

Now the `employees` table contains an additional `email` column.

## Add another column

```sql
ALTER TABLE employees
ADD phone_number VARCHAR(20);
```

## Rename a column

The syntax depends on the database.

For PostgreSQL:

```sql
ALTER TABLE employees
RENAME COLUMN phone_number TO mobile_number;
```

## Rename the table

```sql
ALTER TABLE employees
RENAME TO employee_details;
```

After this command, the table name changes from:

```text
employees
```

to:

```text
employee_details
```

---

# 3. DROP

`DROP` is used to **remove a database object completely**.

## Drop a table

```sql
DROP TABLE employee_details;
```

This removes the table and its data.

After executing the command, the table no longer exists.

### Important

`DROP` is different from `DELETE`.

```sql
DROP TABLE employees;
```

removes the **entire table structure and data**.

Whereas:

```sql
DELETE FROM employees;
```

removes rows but keeps the table structure.

---

# 4. TRUNCATE

`TRUNCATE` is used to **remove all rows from a table while keeping the table structure**.

First, create the table again:

```sql
CREATE TABLE employees (
    employee_id INT,
    employee_name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10,2)
);
```

Insert some data:

```sql
INSERT INTO employees
(employee_id, employee_name, department, salary)
VALUES
(101, 'Rahul', 'IT', 55000.00),
(102, 'Priya', 'HR', 48000.00),
(103, 'Amit', 'Finance', 62000.00);
```

Check the data:

```sql
SELECT * FROM employees;
```

Now use:

```sql
TRUNCATE TABLE employees;
```

Check again:

```sql
SELECT * FROM employees;
```

The table still exists, but it contains **zero rows**.

---

# DROP vs TRUNCATE

| Command  | Removes Data | Removes Table Structure |
| -------- | -----------: | ----------------------: |
| DROP     |          Yes |                     Yes |
| TRUNCATE |          Yes |                      No |
| DELETE   |          Yes |                      No |

### Example

```sql
DROP TABLE employees;
```

The table is completely removed.

```sql
TRUNCATE TABLE employees;
```

All rows are removed, but the table remains.

```sql
DELETE FROM employees;
```

Rows are removed according to the DELETE condition.

---

# Complete DDL Practice Example

## Step 1 – Create table

```sql
CREATE TABLE employees (
    employee_id INT,
    employee_name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10,2)
);
```

## Step 2 – Add data

```sql
INSERT INTO employees
(employee_id, employee_name, department, salary)
VALUES
(101, 'Rahul', 'IT', 55000.00),
(102, 'Priya', 'HR', 48000.00),
(103, 'Amit', 'Finance', 62000.00);
```

## Step 3 – Add a column

```sql
ALTER TABLE employees
ADD email VARCHAR(100);
```

## Step 4 – Check the table

```sql
SELECT * FROM employees;
```

## Step 5 – Remove all data

```sql
TRUNCATE TABLE employees;
```

## Step 6 – Remove the table

```sql
DROP TABLE employees;
```

---

# Interview Questions

### Q1. What is DDL?

DDL stands for Data Definition Language. It is used to define and modify the structure of database objects such as tables.

### Q2. What are the main DDL commands?

The main DDL commands are:

```text
CREATE
ALTER
DROP
TRUNCATE
```

### Q3. What is the difference between DROP and TRUNCATE?

`DROP` removes the complete table including its structure and data.

`TRUNCATE` removes all rows but keeps the table structure.

### Q4. What is ALTER used for?

`ALTER` is used to modify the structure of an existing table, such as adding, modifying, or renaming columns.

### Q5. Can we SELECT from a table after TRUNCATE?

Yes. The table still exists, but there will be no rows.

```sql
TRUNCATE TABLE employees;

SELECT * FROM employees;
```

The result will contain zero rows.

---

# Quick Revision

```text
DDL
 |
 +-- CREATE     → Create table/object
 |
 +-- ALTER      → Modify table structure
 |
 +-- TRUNCATE   → Remove all rows, keep structure
 |
 +-- DROP       → Remove table/object completely
```
