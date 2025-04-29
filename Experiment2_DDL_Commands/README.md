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
-- Create a table named Departments with the following columns:

DepartmentID as INTEGER
DepartmentName as TEXT
For example:

```sql
--
create table Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**
![Screenshot 2025-04-29 082728](https://github.com/user-attachments/assets/fb35f24d-949b-4521-8fe6-46d744d5330d)


**Question 2**
---
-- Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0

```sql
-- 
create table Invoices(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
DueDate DATE check(DueDate>InvoiceDate),
Amount REAL check (Amount>0)
);
```

**Output:**
![Screenshot 2025-04-29 082904](https://github.com/user-attachments/assets/c27a5da3-26a1-4f31-b42f-c55e5c65e6f4)



**Question 3**
---
-- Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```sql
--
insert into Employee(EmployeeID,Name,Position,Department,Salary)
values(001,'Sarah Parker','Manager','HR',60000);
```

**Output:**

![Output3]![Screenshot 2025-04-29 083050](https://github.com/user-attachments/assets/c1ff9c39-7472-4324-b96a-7d532346713a)


**Question 4**
---
--
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
--
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE NOT NULL,
SupplierID INTEGER NOT NULL,
OrderId INTEGER NOT NULL,
FOREIGN KEY (SupplierId)REFERENCES Suppliers(SupplierId),
FOREIGN KEY (OrderId) REFERENCES Orders(OrderID)
);
```

**Output:**

![Output4]![Screenshot 2025-04-29 083236](https://github.com/user-attachments/assets/ac3fddba-1f15-4187-9322-051088f8554f)


**Question 5**
---
--
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

```sql
--
INSERT INTO Customers(CustomerID, Name, Address,Email)
SELECT CustomerID,Name, Address, Email
FROM Old_customers;
```

**Output:**

![Output5]![Screenshot 2025-04-29 083402](https://github.com/user-attachments/assets/de4840bc-7ff3-403a-a28c-8c02f26fd719)


**Question 6**
---
--
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

RollNo      Name            Gender      Subject      MARKS
----------  ------------    ----------  ----------   ----------
205         Olivia Green    F
207         Liam Smith      M           Mathematics  85
208         Sophia Johnson  F           Science

```sql
--
INSERT INTO Student_details (RollNo,Name ,Gender, Subject,MARKS)
VALUES(205, 'Olivia Green','F',NULL,NULL),
(207 ,'Liam Smith','M','Mathematic',85),
(208,'Sophia Johns','F','Science',NULL);
```

**Output:**

![Output6]![Screenshot 2025-04-29 083536](https://github.com/user-attachments/assets/2cd20d3c-41c4-45bd-b097-e4b976d4e694)


**Question 7**
---
-- 
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
--
create table item(
item_id TEXT primary key,
item_desc TEXT NOT NULL,
rate INT NOT NULL,
icom_id TEXT (4),
foreign key(icom_id)REFERENCES company (com_id)
on update cascade
on delete cascade
);
```

**Output:**

![Output7]![Screenshot 2025-04-29 083709](https://github.com/user-attachments/assets/baa4d910-896e-4de3-9d34-59dce13b39b9)


**Question 8**
---
-- 
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
--
create table jobs(
job_id INTEGER,
job_title TEXT ,
min_salary INTEGER DEFAULT 8000,
max_salary INTEGER DEFAULT NULL
);
```

**Output:**

![Output8]![Screenshot 2025-04-29 084046](https://github.com/user-attachments/assets/c3bf9ec9-c9d5-4d18-8ee3-b53cd0e8a523)


**Question 9**
---
--
Write a SQL Query  to add attribute Date_of_joining as Date and rename the attribute job_title as Designation in the table 'Employees'

```sql
-
ALTER TABLE Employees
ADD Date_of_joining  Date;

ALTER TABLE Employees
RENAME COLUMN job_title TO Designation;

```

**Output:**

![Output9]![Screenshot 2025-04-29 084308](https://github.com/user-attachments/assets/71b91683-b9ec-4a0f-9f56-aa85e9523d33)


**Question 10**
---
--
Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
 

```sql
--
ALTER TABLE customer
Add column discount DECIMAL(5,2);
```

**Output:**

![Output10]![Screenshot 2025-04-29 084424](https://github.com/user-attachments/assets/731268a8-83f9-4349-a575-c82322010305)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
