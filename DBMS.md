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
   - 1.12 [DBMS vs RDBMS](#dbms-vs-rdbms)
   - 1.13 [SQL vs NoSQL](#sql-vs-nosql)
2. [SQL](#2-sql)
   - [Overview](#sql)
   - [Commands (DDL, DML, DCL, TCL)](#sql-commands)
   - [Joins](#joins)
   - [Subqueries](#subqueries)
   - [Indexes and Views](#indexes-and-views)
   - [Aggregate Functions](#aggregate-functions)

3. [MONGODB](#3-mongodb)
   - [Overview](#mongodb)
   - [Collections and Documents](#collections-and-documents)
   - [CRUD Operations](#crud-operations)
   - [Aggregation](#aggregation)
   - [Indexes in MongoDB](#indexes-in-mongodb)
   - [SQL vs MongoDB](#sql-vs-mongodb)
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
A transaction is a small unit of work in a database that performs one complete task.
Either the whole task happens, or none of it happens.

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
- Consistency mean  Database must always remain valid.  
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


