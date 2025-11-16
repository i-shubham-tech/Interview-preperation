# Database And Management System

# 📘 Table of Contents

1. [DBMS Basics](#1-dbms-basics)
   - 1.1 [Database](#database)
   - 1.2 [DBMS](#dbms)
   - 1.3 [DBMS vs File System](#dbms-vs-file-system)
   - 1.4 [Data Model and Its Types](#data-model-and-its-types)
   - 1.5 [Schema vs Instance](#schema-vs-instance)
   - 1.6 [Keys in DBMS](#keys-in-dbms)
   - 1.7 [Constraints](#constraints)
   - 1.8 [Normalization (1NF, 2NF, and 3NF)](#18--normalization-1nf-2nf-and-3nf)
   - 1.9 [Denormalization](#19-denormalization)
   - 1.10 [Transaction](#110-transaction)
   - 1.11 [ACID Properties](#111-acid-properties-of-a-transaction)
   - 1.12 [DBMS vs RDBMS](#112-dbms-vs-rdbms)
   - 1.13 [SQL vs NoSQL](#113-sql-vs-nosql)
2. [SQL](#2-sql)
   - [Overview](#sql)
   - [Commands (DDL, DML, DCL, TCL)](#sql-commands)
   - - DDL
     - DML
     - DQL
     - DCL
     - TCL
   - [Condition Clause](#sql-commands)
   - [Order By](#sql-commands)
   - [Group By](#sql-commands)
   - [Aggregate Functions](#aggregate-functions)
   - [Subqueries](#subqueries)
   - [Joins](#joins)
   - [Indexes and Views](#indexes-and-views)
  
3. [MONGODB](#3-mongodb)
   - [ MongoDB Definition & Basic Concepts](#mongodb)
   - [Insert Document](#collections-and-documents)
   - [Update Document](#crud-operations)
   - [Delete Document](#aggregation)
   - [Find Document](#aggregation)
   - [Comparison Operators](#indexes-in-mongodb)
   - [MongoDB Aggregation](#sql-vs-mongodb)
---
# 1. DBMS Basics

## Database

### 🔹 Definition

A **database** is an organized collection of data that store and access electronically.  
its manage by dbms which ensure integrity ,support query and allow efficient data management and retrival

### 🔹 Example
Imagine a **student database** in a college:
| Student_ID | Name     | Age | Course   |
|-------------|----------|-----|----------|
| 101         | Riya     | 20  | BCA      |
| 102         | Aarav    | 21  | B.Tech   |
| 103         | Meena    | 19  | BBA      |

Here, all student information is stored together — this is a **database**.

---
## 2. DBMS 
A **Database Management System (DBMS)** is software that helps **store, manage, and retrival  data** efficiently in a database.  
It acts as an **interface** between the user and the database.

### 🔹 Example
Examples of DBMS software:
- MySQL  
- MONGODB
- Oracle  
- PostgreSQL  
- Microsoft Access  
- SQLite  

---

## 3. File System vs DBMS


| **Feature** | **File System** | **DBMS** |
|--------------|-----------------|-----------|
| **Data Storage** | Stores data in separate files | Stores data in structured databases |
| **Redundancy** | High duplication | Controlled redundancy |
| **Security** | Limited (file-level) | Strong access control |
| **Data Integrity** | Hard to maintain | Enforced via constraints |
| **Backup & Recovery** | Manual | Automatic |
| **Data Sharing** | Difficult | Multi-user access supported |

---

## 4. Data Model and Its Types

### 🔹 Definition
A **data model** defines how data is **organized, stored, and related** within a database.  

| Type | Description | Example |
|------|--------------|----------|
| **Hierarchical Model** |The Hierarchical Data Model organizes data in a tree-like structure where each child record has only one parent, but a parent can have multiple children.It represents one-to-many relationships and is fast for hierarchical data retrieval.. | Employee → Department |
| **Network Model** | The Network Data Model organizes data in a graph structure where each record can have multiple parent or children..It supports many-to-many relationships and provides more flexibility than the hierarchical model.. | Student ↔ Course |
| **Relational Model** | The Relational Data Model organizes data into tables (relations) made of rows and columns, where each row represents a record and each column represents an attribute.Relationships are defined using keys (primary and foreign), and data can be queried using SQL.. | MySQL, PostgreSQL |
| **Entity-Relationship (ER) Model** | The Entity–Relationship Model is a conceptual design model that represents how data organised  of a system using entities, attributes, and relationships.It is mainly used to visually design and plan relational databases through ER diagrams. | ER Diagram |
| **Object-Oriented Model** | The Object-Oriented Data Model represents data in the form of objects, similar to object-oriented programming.Each object contains data (attributes) and behavior (methods), and it supports concepts like inheritance, encapsulation, and polymorphism for better real-world modeling.. | ObjectDB |

---

## 6. Keys in DBMS

### 🔹 Definition
A **key** is an attribute (or set of attributes) that helps **uniquely identify** a record in a table.

### 🔹 Types of Keys

| Key | Description | Example |
|------|--------------|----------|
| **Super Key** | A set of attributes that can uniquely identify a record. | (ID), (ID, Name) |
| **Candidate Key** | Minimal super key — no extra attributes. | (ID) |
| **Primary Key** | Main key chosen to uniquely identify records. | Student_ID |
| **Alternate Key** | Candidate keys not chosen as the primary key. | Roll_No |
| **Foreign Key** | Attribute that refers to a primary key of another table. | Dept_ID in Employee table |
| **Composite Key** | Key formed by combining two or more attributes. | (Student_ID, Course_ID) |

---

## 7. Constraints

### 🔹 Definition
A **constraint** is a rule applied to table data to **ensure accuracy, validity, and integrity**.

### 🔹 Common Types of Constraints

| Constraint | Description | Example |
|-------------|--------------|----------|
| **NOT NULL** | Ensures a column cannot have a NULL value. | Name VARCHAR(50) NOT NULL |
| **UNIQUE** | Ensures all values in a column are unique. | Email UNIQUE |
| **PRIMARY KEY** | Uniquely identifies each record. | PRIMARY KEY(Student_ID) |
| **FOREIGN KEY** | Links one table to another. | FOREIGN KEY(Dept_ID) REFERENCES Department(Dept_ID) |
| **CHECK** | Ensures values meet a specific condition. | CHECK(Age >= 18) |
| **DEFAULT** | Assigns a default value if none provided. | DEFAULT 'India' |

---

## 1.8  Normalization (1NF, 2NF, and 3NF)

### 📌 What is Normalization?
Normalization is a process of organizing data in a database to:
- Reduce redundancy (duplicate data)
- Improve data integrity(accurate and consistent)
- Ensure logical data dependencies

### 🔹 1NF – First Normal Form
**Rule:**  
- Each column attribute should contain **atomic (indivisible)** values (no attribute have multivalue).
- 
**Example (Not in 1NF):**
| Student | Phone           |
|---------|----------------|
| Rahul   | 9876, 9123     |

❌ Phone contains multiple values.

**Corrected (1NF):**
| Student | Phone |
|---------|--------|
| Rahul   | 9876   |
| Rahul   | 9123   |


### 🔹 2NF – Second Normal Form  
**Rules:**  
- Must be in **1NF**  
- There should not be **partial dependency** i.e (If a table has a composite primary key then every non-key attribute must depend on the entire key, not just one part of it.
  
**Example (Not in 2NF):**
Composite Key → (StudentID, CourseID)

| StudentID | CourseID | StudentName |
|------------|----------|--------------|
| 1          | 101      | Rahul        |
| 1          | 102      | Rahul        |
| 2          | 101      | Harsh        |

❌ StudentName depends only on StudentID (part of the key)

**Corrected (2NF):**
**Student Table**
| StudentID | StudentName |
|-----------|-------------|
| 1         | Rahul       |
| 2         | Harsh       |

**Enrollment Table**
| StudentID | CourseID |
|-----------|-----------|
| 1         | 101       |
| 1         | 102       |
| 2         | 101       |


### 🔹 3NF – Third Normal Form  
**Rules:**  
- Must be in **2NF**  
- There should not be **transitive dependency** (i.e No non-key column depends on another non-key column.)

**Example (Not in 3NF):**
| StudentID | DeptID | DeptName |
|------------|---------|-----------|
| 1          | D1      | Computer  |
| 2          | D1      | Computer  |
| 3          | D2      | Electronid  |

❌ StudentID → DeptID  → DeptName (departent id depand on student id and dep  name depand on dep id)

**Corrected (3NF):**

**Student Table**
| StudentID | DeptID |
|------------|---------|
| 1          | D1      |
| 2          | D1      |
| 3          | D2      |

**Department Table**
| DeptID | DeptName |
|---------|-----------|
| D1      | Computer |
| D2      | Electronics |

### 📌 Summary Table  
| Normal Form | Removes | Rule |
|--------------|----------|-------|
| **1NF** | Multivalue attritbute | Atomic values only |
| **2NF** | Partial dependency | Full dependency on whole key |
| **3NF** | Transitive dependency | Non-key attributes depend only on key |

---

## 1.9 Denormalization

### 📌 What is Denormalization?
Denormalization is the process of **intentionally combining normalized tables** to improve **read performance**.  
it is done 
- To improve read performance
- To reduce complex joins
- To make queries faster in large databases

### 🛠️ Example
**Normalized Tables (3NF):**

**Student Table**
| StudentID | DeptID |
|-----------|---------|
| 1         | D1      |

**Department Table**
| DeptID | DeptName |
|--------|-----------|
| D1     | Computer |

To fetch Student + Department name → Requires JOIN.

**Denormalized Table:**

| StudentID | DeptID | DeptName |
|-----------|---------|-----------|
| 1         | D1      | Computer  |

👉 Faster reads, no JOIN needed  
❌ But DeptName is stored multiple times → redundancy

---

## 1.10 Transaction

### 📌 What is Transaction?
A transaction is a small unit of work in a database that performs one complete task where either the whole task happens, or none of it happens.

### Why Transactions Are Important?

- Maintain data integrity
- Prevent data loss
- Ensure consistent results in multi-user environments

### Example

```
Suppose you send ₹500 to your friend:
This involves two steps:
- Money deducted from your account
- Money added to your friend's account
These two steps together = one transaction.

If any step fails → the whole transaction is cancelled (rolled back).
```
---
## 1.11 ACID Properties of a Transaction
ACID properties makes sure a transaction is safe, correct, and reliable.

### 1. **Atomicity**
- A transaction is **all-or-nothing**.  
- If any part fails, the entire transaction is rolled back.

### 2. **Consistency**
- Consistency mean database must always remain in valid State.  
- It should follow all rules, constraints, and data integrity conditions before and after a transaction..
- Example : Negative Balance Not Allowed


### 3. **Isolation**
- Isolation ensures that even if multiple transactions run at the same time, they do not affect each other.
- Each transaction behaves as if it is running alone until it is completed.


### 4. **Durability**
- Once a transaction is committed, changes are **permanent** even in case of system failure.


## ✔️ Example of a Transaction in SQL
```sql
BEGIN TRANSACTION;

UPDATE Account SET Balance = Balance - 500 WHERE AccNo = 101;
UPDATE Account SET Balance = Balance + 500 WHERE AccNo = 202;

COMMIT;
```
---
## 1.12 DBMS vs RDBMS

| **Feature** | **DBMS** | **RDBMS** |
|--------------|-----------|-------------|
| Data Storage | Stores data as files or hierarchical/network formats | Stores data in tables (rows & columns) |
| Relationships | Doesn’t support relationships between data | Supports relationships using foreign keys |
| Normalization | Limited or no support | Fully supports normalization |
| Integrity Constraints | Not strictly enforced | Enforced using PK, FK, and constraints |
| Multi-user Support | Limited | Strong multi-user support with ACID properties |

---
## 1.13 SQL vs NoSQL

| **Feature** | **SQL Databases** | **NoSQL Databases** |
|--------------|--------------------|------------------------|
| Data Model | Relational (tables) | Non-relational (document, key-value, graph, column) |
| Schema | Fixed, predefined schema | Schema-less, flexible |
| Scalability | Vertical scaling | Horizontal scaling |
| Query Language | Uses SQL | Uses different query mechanisms (JSON, APIs, etc.) |
| Best For | Complex queries & transactions | Big data, high-speed reads/writes, unstructured data |

---
# SQL

## 1️⃣ What is SQL?
**SQL (Structured Query Language)** is a standard language used to store, retrieve, manage, and manipulate data in relational databases.
Common SQL databases: **MySQL, PostgreSQL, Oracle, SQL Server**

---

## 2️⃣ Types of SQL Commands
SQL commands are divided into the following categories:

- DDL – Data Definition Language
- DML – Data Manipulation Language
- DQL – Data Query Language
- DCL – Data Control Language
- TCL – Transaction Control Language

---

## DDL – Data Definition Language
Used to define or modify database structure.
- `CREATE`
- `ALTER`
- `DROP`
- `TRUNCATE`

### 1️⃣ Create

####  Definition
`CREATE` is used to **create** a new database object such as a table, database, view, or index.

#### Syntax
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);
```
#### Example
```sql
CREATE TABLE Student (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);
```

### 2️⃣ ALTER

#### Definition
`ALTER` is used to **modify an existing table structure**, such as adding, deleting, or changing columns.

#### Syntax
```sql
ALTER TABLE table_name
ADD/MODIFY/DROP column_name datatype;

```
#### Example
```sql
ALTER TABLE Student
ADD email VARCHAR(100);

```

### 3️⃣ DROP

#### Definition
`DROP` is used to **permanently delete** a database object such as a table, database, view, or index.  
This action removes both **structure and data**.

#### Syntax
```sql
DROP TABLE table_name;
```
#### Example
```sql
DROP TABLE Student;
```

### 4️⃣ TRUNCATE

#### Definition
`TRUNCATE` is used to **remove all rows** from a table quickly while keeping the table structure intact.  
It cannot be rolled back in many databases.

#### Syntax
```sql
TRUNCATE TABLE table_name;
```

#### Example
```sql
TRUNCATE TABLE Student;
```

---
  

## DML – Data Manipulation Language
Used to manipulate data inside tables.
- `INSERT`
- `UPDATE`
- `DELETE`

### 1️⃣ INSERT

#### Definition
`INSERT` is used to **add new records (rows)** into a table.

#### Syntax
```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

#### Example
```sql
INSERT INTO Student (id, name, age)
VALUES (1, 'Rahul', 20);
```

### 2️⃣ UPDATE

#### Definition
`UPDATE` is used to **modify existing records** in a table.

#### Syntax
```sql
UPDATE table_name
SET column_name = value
WHERE condition;
```

#### Example
```sql
UPDATE Student
SET age = 21
WHERE id = 1;
```

### 3️⃣ DELETE

#### Definition
`DELETE` is used to **remove specific rows** from a table based on a condition.

#### Syntax
```sql
DELETE FROM table_name
WHERE condition;
```
#### Example
```sql
DELETE FROM Student
WHERE id = 1;
```
---

## 🔹 DQL – Data Query Language
Used to fetch data.
- `SELECT`

### SELECT Command

#### Definition
`SELECT` is used to **retrieve/read data** from one or more tables in a database.

#### Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

#### example
```sql
SELECT name, salary
FROM employees
WHERE salary > 50000;
```
---


### 🔹DCL - Data Control Language
Controls permissions.
- `GRANT`
- `REVOKE`

### Common Privileges

| Privilege        | Meaning                  |
|------------------|---------------------------|
| `SELECT`         | Read data                 |
| `INSERT`         | Add new data              |
| `UPDATE`         | Modify existing data      |
| `DELETE`         | Remove data               |
| `ALL PRIVILEGES` | Gives full access         |

### GRANT Command

#### Definition
`GRANT` is used to **give permissions** to a user or role so they can perform specific actions on a database object (table, view, schema, etc.).

#### Syntax
```sql
GRANT privilege_name
ON object_name
TO user_name;
```

#### example
```sql
➤ Give Particular permission on a table
GRANT SELECT ON employees TO user1;

➤ Give multiple permissions
GRANT SELECT, INSERT, UPDATE ON products TO user1;

➤ Grant ALL permissions
GRANT ALL PRIVILEGES ON sales TO admin_user;

➤ Grant privileges to a role
GRANT SELECT ON employees TO hr_role;

```

### REVOKE Command

#### Definition
`REVOKE` is used to **remove permissions** that were previously granted to a user or role.


#### Syntax
```sql
REVOKE privilege_name
ON object_name
FROM user_name;
```

#### example

```sql
Revoke SELECT permission
REVOKE SELECT ON employees FROM user1;

➤ Revoke multiple permissions
REVOKE SELECT, INSERT, UPDATE ON products FROM user1;

➤ Revoke ALL permissions
REVOKE ALL PRIVILEGES ON sales FROM admin_user;

➤ Revoke permission from a role
REVOKE SELECT ON employees FROM hr_role;
```
---

## TCL – Transaction Control Language
Manages transactions.
- `COMMIT`
- `ROLLBACK`
- `SAVEPOINT`


### COMMIT Command

#### Definition
`COMMIT` is used to **save all changes permanently** in the database.

#### Syntax
```sql
COMMIT;
```

#### example

```sql
UPDATE employees SET salary = salary + 5000;
COMMIT;   -- changes are permanently saved
```

### ROLLBACK Command

#### Definition
`ROLLBACK` is used to undo changes made in the current transaction (before COMMIT).

#### Syntax
```sql
ROLLBACK;
```

#### example

```sql
DELETE FROM employees WHERE id = 5;
ROLLBACK;   -- delete operation undone
```

### SAVEPOINT Command

#### Definition
`SAVEPOINT` is used to **set a checkpoint** within a transaction, allowing you to roll back only part of the transaction instead of the entire operation.

#### Syntax
```sql
SAVEPOINT savepoint_name;
```

#### example

```sql
BEGIN;
UPDATE employees SET salary = 60000 WHERE id = 1;
SAVEPOINT sp1;   -- checkpoint created
UPDATE employees SET salary = 70000 WHERE id = 2;
ROLLBACK TO sp1;   -- undo second update, first update remains
COMMIT;   -
```
---

## WHERE Clause Condition

| Category                         | Operator / Keyword | Meaning                              |
|----------------------------------|---------------------|--------------------------------------|
| **Comparison Operators**         | `=`                 | Equal to                             |
|                                  | `!=` or `<>`        | Not equal to                         |
|                                  | `>`                 | Greater than                         |
|                                  | `<`                 | Less than                            |
|                                  | `>=`                | Greater than or equal to             |
|                                  | `<=`                | Less than or equal to                |
| **Logical Operators**            | `AND`               | Both conditions must be true         |
|                                  | `OR`                | Either condition can be true         |
|                                  | `NOT`               | Negates a condition                  |
| **Range / Set / Pattern**        | `BETWEEN … AND …`   | Value lies within a range            |
|                                  | `IN ( … )`          | Matches any value from a set         |
|                                  | `NOT IN ( … )`      | Excludes values from a set           |
|                                  | `LIKE`              | Pattern matching                     |
|                                  | `NOT LIKE`          | Excludes pattern matching            |
| **NULL Operators**               | `IS NULL`           | Value is NULL                        |
|                                  | `IS NOT NULL`       | Value is not NULL                    |

### Example

```example
-- Fetch all columns
SELECT * FROM employees;

-- Fetch selected columns
SELECT name, salary FROM employees;

-- WHERE with comparison
SELECT name FROM employees WHERE salary > 50000;

-- WHERE with =
SELECT * FROM students WHERE city = 'Mumbai';

-- WHERE with != / <>
SELECT * FROM students WHERE grade <> 'A';

-- AND operator
SELECT * FROM employees WHERE department = 'IT' AND salary > 60000;

-- OR operator
SELECT * FROM employees WHERE department = 'IT' OR department = 'HR';

-- NOT operator
SELECT * FROM employees WHERE NOT department = 'Sales';

-- BETWEEN
SELECT * FROM products WHERE price BETWEEN 100 AND 500;

-- IN
SELECT * FROM employees WHERE department IN ('IT', 'HR', 'Finance');

-- NOT IN
SELECT * FROM employees WHERE department NOT IN ('Sales', 'Support');

-- LIKE (starts with)
SELECT * FROM customers WHERE name LIKE 'A%';

-- LIKE (ends with)
SELECT * FROM customers WHERE name LIKE '%n';

-- LIKE (contains)
SELECT * FROM customers WHERE name LIKE '%ar%';

-- IS NULL
SELECT * FROM orders WHERE discount IS NULL;

-- IS NOT NULL
SELECT * FROM orders WHERE discount IS NOT NULL;

```
---

## ORDER BY

### Definition
`ORDER BY` is used to **sort the result** of a query in **ascending (ASC)** or **descending (DESC)** order.

###  Syntax
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column_name ASC | DESC;
```

### Examples

```
➤ Sort in ascending order (default)
SELECT name, salary
FROM employees
ORDER BY salary;

➤ Sort in descending order
SELECT name, salary
FROM employees
ORDER BY salary DESC;

➤ Sort by multiple columns
SELECT name, department, salary
FROM employees
ORDER BY department ASC, salary DESC;
```
---

## Aggregate Functions in SQL

### Definition
Aggregate functions perform **calculations on a group of rows** and return a **single value** (often used with GROUP BY).


### Common Aggregate Functions

| Function | Meaning |
|----------|---------|
| `COUNT()` | Returns the number of rows |
| `SUM()` | Returns the total sum of a numeric column |
| `AVG()` | Returns the average value |
| `MAX()` | Returns the maximum value |
| `MIN()` | Returns the minimum value |


### ✅ 3. Examples

```sql

### ➤ COUNT()
SELECT COUNT(*) AS total_employees
FROM employees;

➤ SUM()
SELECT SUM(salary) AS total_salary
FROM employees;

➤ AVG()
SELECT AVG(salary) AS average_salary
FROM employees;

➤ MAX()
SELECT MAX(salary) AS highest_salary
FROM employees;

➤ MIN()
SELECT MIN(salary) AS lowest_salary
FROM employees;
```
---

## GROUP BY

###  Definition
`GROUP BY` is used to **group rows** that have the same values in specified columns and is usually combined with **aggregate functions** like COUNT, SUM, AVG, MAX, MIN.

###  Syntax
```sql
SELECT column_name, aggregate_function(column)
FROM table_name
GROUP BY column_name;
```

### Example

```
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```
---
## HAVING Clause

### ✅ Definition
The **HAVING** clause is used to filter groups after the `GROUP BY` operation.  
It is mainly used with aggregate functions like **SUM**, **COUNT**, **AVG**, **MAX**, and **MIN**.

> `WHERE` filters **rows before grouping**
> `HAVING` filters **groups after grouping**

### 🧠 Syntax
```sql
SELECT column, AGG_FUNC(column)
FROM table_name
GROUP BY column
HAVING condition;
```
### Example
```
SELECT department, SUM(salary) AS total_salary
FROM employees
GROUP BY department
HAVING SUM(salary) > 100000;
```

## LIMIT

### Definition
`LIMIT` is used to **restrict the number of rows** returned by a query.

### Syntax
```sql
SELECT column1, column2
FROM table_name
LIMIT number;
```
### Example
```
➤ Fetch first 5 rows
SELECT * 
FROM employees
LIMIT 5;
```

## 🪟 Window Functions (SQL)

### ✅ Definition
A **Window Function** performs a calculation across a set of rows that are related to the current row **without grouping the rows**.  
It works like an “advanced analytical function” used for ranking, running totals, moving averages, etc.

| Function       | Meaning                              |
|----------------|----------------------------------------|
| `ROW_NUMBER()` | Gives row number within each partition |
| `RANK()`       | Assigns rank with gaps                 |
| `DENSE_RANK()` | Assigns rank without gaps              |
| `SUM()`        | Running total                          |
| `AVG()`        | Moving average                         |
| `LAG()`        | Value from previous row                |
| `LEAD()`       | Value from next row                    |

### 🔧 Syntax
```sql
FUNCTION_NAME(column) OVER (
    PARTITION BY column
    ORDER BY column
)
```

### 1️⃣ ROW_NUMBER()

Purpose: Gives sequential row number within each partition.
```
SELECT 
    name,
    department,
    salary,
    ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC) AS row_num
FROM employees;
```

### 2️⃣ RANK()

Purpose: Assigns rank with gaps when values tie.

```SELECT
    name,
    salary,
    RANK() OVER (ORDER BY salary DESC) AS salary_rank
FROM employees;
```

### 3️⃣ DENSE_RANK()

Purpose: Assigns rank without gaps for ties.

```SELECT
    name,
    salary,
    DENSE_RANK() OVER (ORDER BY salary DESC) AS salary_dense_rank
FROM employees;
```

### 4️⃣ SUM() — Running Total

Purpose: Running total of values.
```
SELECT 
    order_id,
    amount,
    SUM(amount) OVER (ORDER BY order_id) AS running_total
FROM orders;
```

### 5️⃣ AVG() — Moving Average

Purpose: Average calculated over a sliding window.
```
SELECT
    date,
    sales,
    AVG(sales) OVER (ORDER BY date ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS moving_avg
FROM daily_sales;
```


### 6️⃣ LAG()

Purpose: Value from previous row.
```
SELECT
    date,
    sales,
    LAG(sales, 1) OVER (ORDER BY date) AS previous_day_sales
FROM daily_sales;
```

### 7️⃣ LEAD()

Purpose: Value from next row.

```
SELECT
    date,
    sales,
    LEAD(sales, 1) OVER (ORDER BY date) AS next_day_sales
FROM daily_sales;
```
---
# MongoDB

## 1. MongoDB Definition & Basic Concepts

| Concept         | Explanation                                                                           |
| --------------- | ------------------------------------------------------------------------------------- |
| **MongoDB**     | A NoSQL, document-oriented database that stores data in flexible JSON-like documents. |
| **Database**    | A container for collections.                                                          |
| **Collection**  | A group of related documents (like a table).                                          |
| **Document**    | A record in MongoDB stored in BSON (Binary JSON) format.                              |
| **Field**       | A key-value pair inside a document.                                                   |
| **_id**         | A unique identifier automatically created for each document.                          |
| **Schema-less** | No fixed structure; each document can have different fields.                          |
| **NoSQL**       | Non-relational, highly scalable database.                                             |

---

## 2. Insert Document

### ➤ `insertOne()`

```js
// Insert a single document
 db.users.insertOne({ name: "Shubham", age: 22, city: "Delhi" });
```

### ➤ `insertMany()`

```js
// Insert multiple documents
 db.users.insertMany([
   { name: "Aman", age: 25 },
   { name: "Riya", age: 23 }
 ]);
```

---

## 3. Update Document

### ➤ `updateOne()`

```js
// Update first matching document
 db.users.updateOne(
   { name: "Shubham" },
   { $set: { city: "Mumbai" } }
 );
```

### ➤ `updateMany()`

```js
// Update all matching documents
 db.users.updateMany(
   { age: { $gt: 20 } },
   { $set: { active: true } }
 );
```

---

## 4. Delete Document

### ➤ `deleteOne()`

```js
// Delete first matching
 db.users.deleteOne({ name: "Aman" });
```

### ➤ `deleteMany()`

```js
// Delete multiple
 db.users.deleteMany({ age: { $lt: 18 } });
```

---

## 5. Find Document

### ➤ `findOne()`

```js
 db.users.findOne({ name: "Shubham" });
```

### ➤ `find()`

```js
// Find all documents
 db.users.find();

// With condition
 db.users.find({ city: "Delhi" });
```

---

## 6. Comparison Operators

| Operator | Meaning               | Example                                  |
| -------- | --------------------- | ---------------------------------------- |
| `$eq`    | Equal to              | `{ age: { $eq: 25 } }`                   |
| `$ne`    | Not equal             | `{ age: { $ne: 25 } }`                   |
| `$gt`    | Greater than          | `{ age: { $gt: 18 } }`                   |
| `$gte`   | Greater than or equal | `{ age: { $gte: 18 } }`                  |
| `$lt`    | Less than             | `{ age: { $lt: 30 } }`                   |
| `$lte`   | Less than or equal    | `{ age: { $lte: 30 } }`                  |
| `$in`    | Matches any in array  | `{ city: { $in: ["Delhi", "Mumbai"] } }` |
| `$nin`   | Not in array          | `{ city: { $nin: ["Delhi"] } }`          |

---

## 7. MongoDB Aggregation (Basics)

Aggregation is used for complex data processing like filtering, grouping, sorting, summing, etc.

### ➤ Simple Aggregation Pipeline

```js
 db.users.aggregate([
   { $match: { city: "Delhi" } },
   { $group: { _id: "$city", totalUsers: { $sum: 1 } } }
 ]);
```

### ➤ Common Aggregation Operators

| Operator   | Explanation                     |
| ---------- | ------------------------------- |
| `$match`   | Filters documents (like WHERE). |
| `$group`   | Groups documents by field.      |
| `$sort`    | Sorts results.                  |
| `$project` | Selects specific fields.        |
| `$limit`   | Limits number of documents.     |
| `$sum`     | Calculates sum.                 |
| `$avg`     | Calculates average.             |
| `$count`   | Counts documents.               |

---

If you want, I can also create **Indexing, Joins (lookup), CRUD cheatsheet, or Full MongoDB revision sheet** in .md.

---

## 8. Indexing in MongoDB

Indexing improves query performance by creating a special data structure that makes searching faster.

### ➤ Create Index

```js
// Create index on 'name' field
 db.users.createIndex({ name: 1 }); // 1 = ascending
```

### ➤ Compound Index

```js
// Index on multiple fields
 db.users.createIndex({ name: 1, age: -1 });
```

### ➤ Unique Index

```js
 db.users.createIndex({ email: 1 }, { unique: true });
```

### ➤ Drop Index

```js
 db.users.dropIndex({ name: 1 });
```

### ➤ Types of Indexes

| Index Type             | Explanation               |
| ---------------------- | ------------------------- |
| **Single Field Index** | Index on one field        |
| **Compound Index**     | Index on multiple fields  |
| **Unique Index**       | Prevents duplicate values |
| **Text Index**         | For full-text search      |
| **Hashed Index**       | Used for sharding         |

---

## 9. Lookup (Joins in MongoDB)

`$lookup` is used to join two collections (similar to LEFT JOIN in SQL).

### ➤ Basic Lookup Example

```js
 db.orders.aggregate([
   {
     $lookup: {
       from: "users",       // collection to join
       localField: "userId", // field in orders
       foreignField: "_id",  // field in users
       as: "userDetails"     // output array
     }
   }
 ]);
```

### ➤ Unwind Joined Array

```js
 db.orders.aggregate([
   { $lookup: { from: "users", localField: "userId", foreignField: "_id", as: "userDetails" } },
   { $unwind: "$userDetails" }
 ]);
```

### ➤ Lookup with Pipeline (Advanced Join)

```js
 db.orders.aggregate([
   {
     $lookup: {
       from: "users",
       let: { uid: "$userId" },
       pipeline: [
         { $match: { $expr: { $eq: ["$_id", "$$uid"] } } },
         { $project: { name: 1, city: 1 } }
       ],
       as: "userData"
     }
   }
 ]);
```

---
