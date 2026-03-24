# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="700" height="600" alt="image" src="https://github.com/user-attachments/assets/f42645be-ef64-4d9d-9b82-46e411b6a5b4" />


```
ALTER TABLE Student_details
ADD COLUMN Country TEXT
```

**Output:**
<img width="1855" height="277" alt="image" src="https://github.com/user-attachments/assets/27937691-0acf-4bcf-b284-c36f70cdbc46" />


**Question 2**
---
<img width="700" height="600" alt="image" src="https://github.com/user-attachments/assets/f8099d36-e74f-41bc-b472-bbf4492e0184" />


```
CREATE TABLE Events
(
    EventID INTEGER,
    EventName TEXT,
    EventDate DATE
);
```

**Output:**

<img width="1911" height="310" alt="image" src="https://github.com/user-attachments/assets/53c76a76-aef8-4e8c-af39-433358c0a70c" />


**Question 3**
---
<img width="700" height="600" alt="image" src="https://github.com/user-attachments/assets/800a1f69-41c9-41d6-a153-f52eed89c7cb" />


```
ALTER TABLE Student_details
ADD COLUMN email TEXT NOT NULL DEFAULT('Invalid')
```

**Output:**

<img width="1899" height="179" alt="image" src="https://github.com/user-attachments/assets/57bc52aa-ac26-4342-ae3d-b854d7c4bf27" />


**Question 4**
---
<img width="700" height="600" alt="image" src="https://github.com/user-attachments/assets/b78f7a87-6f5e-4fd3-a143-525e8110c0a2" />


```
INSERT INTO Products(ProductID,Name,Category)
VALUES(104,"Tablet","Electronics")
```

**Output:**

<img width="1890" height="165" alt="image" src="https://github.com/user-attachments/assets/f5545497-0775-4c9b-b596-53a495e3ae09" />


**Question 5**
---
<img width="700" height="600" alt="image" src="https://github.com/user-attachments/assets/b9c0daa5-c2a9-4f6d-87f5-8ef49121d8ed" />


```
INSERT INTO Employee(EmployeeID,Name,Position)
VALUES(4,"Emily White","Analyst")
```

**Output:**

<img width="1872" height="421" alt="image" src="https://github.com/user-attachments/assets/9d1719f9-2ea0-48b4-9c6c-e72666e5b852" />


**Question 6**
---
<img width="700" height="600" alt="image" src="https://github.com/user-attachments/assets/84c7e9e7-bd47-4349-bcbe-97abcfab53bd" />


```
CREATE TABLE products
(
    product_id INTEGER PRIMARY KEY,
    product_name TEXT NOT NULL,
    list_price DECIMAL(10,2) NOT NULL,
    discount DECIMAL(10,2) NOT NULL DEFAULT 0,
    CHECK(list_price>=discount AND discount>=0 AND list_price>=0)
);
```

**Output:**

<img width="1897" height="187" alt="image" src="https://github.com/user-attachments/assets/aac0318a-199d-4de2-9218-ebe205a4bb7a" />


**Question 7**
---
<img width="700" height="600" alt="image" src="https://github.com/user-attachments/assets/2cd93ed5-59ba-47e2-a222-31e282163f91" />


```
CREATE TABLE Department
(
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
);
```

**Output:**

<img width="1900" height="159" alt="image" src="https://github.com/user-attachments/assets/16723acc-1e64-467f-bfc5-3016e164d65c" />


**Question 8**
---
<img width="1850" height="372" alt="image" src="https://github.com/user-attachments/assets/ef12ab40-a395-4717-a82f-524845307e45" />


```
CREATE TABLE Bonuses
(
    BonusID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    BonusAmount REAL CHECK(BonusAmount>0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY (EMployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1893" height="138" alt="image" src="https://github.com/user-attachments/assets/f6e382b1-880b-4bec-9ccd-1899bed2e886" />


**Question 9**
---
<img width="1063" height="460" alt="image" src="https://github.com/user-attachments/assets/0a957a48-3827-4786-b346-9f317095b78e" />


```
INSERT INTO Student_details(RollNo,Name,Gender)
VALUES(204,"Samuel Black","M")
```

**Output:**

<img width="1745" height="371" alt="image" src="https://github.com/user-attachments/assets/c33e6529-6c59-465c-aef3-9be0991e88f6" />


**Question 10**
---
<img width="927" height="427" alt="image" src="https://github.com/user-attachments/assets/4f65bec8-1a84-4213-9e5e-d7593f8762bb" />


```
CREATE TABLE Employees
(
    EmployeeID INTEGER,
    FirstName TEXT,
    LastName TEXT,
    HireDate DATE
);
```

**Output:**

<img width="1884" height="270" alt="image" src="https://github.com/user-attachments/assets/80ab7386-6c57-46d6-9f3f-8ef6c163e724" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
