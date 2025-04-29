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

Write a SQL query to Add a new column State as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT   0                       0

For example:

Test	Result

pragma table_info('Student_details');

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      int         0                       1
1           Name        VARCHAR(10  1                       0
2           Gender      TEXT        1                       0
3           Subject     VARCHAR(30  0                       0
4           MARKS       INT (3)     0                       0
5           State       TEXT        0                       0

Answer:(penalty regime: 0 %)

ALTER TABLE  Student_details ADD COLUMN State TEXT;

**Output:**

![Screenshot (89)](https://github.com/user-attachments/assets/b1df5810-0e19-4ab9-a5f2-6dac88b9a064)

**Question 2**

Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values.

For example:

Test	Result:

SELECT EmployeeID, Name, Position 
FROM Employee;
EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Answer:(penalty regime: 0 %)

INSERT INTO Employee(EmployeeID,Name,Position)
VALUES('4','Emily White','Analyst');

**Output:**

![Screenshot (90)](https://github.com/user-attachments/assets/5a14486e-98e3-4233-98a7-86192f305325)


**Question 3**
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

For example:

Test	Result

select * from Employee;
EmployeeID  Name        Department  Salary
----------  ----------  ----------  ----------
201         John Doe    HR          50000
202         Jane Smith  Engineerin  75000
203         Emily Davi  Marketing   60000

Answer:(penalty regime: 0 %)

INSERT into Employee(EmployeeID,Name,Department,Salary)
SELECT EmployeeID,Name,Department,Salary FROM Former_employees;

**Output:**

![Screenshot (91)](https://github.com/user-attachments/assets/2a832515-67c3-478a-8c24-bbd618e05942)


**Question 4**
Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME

For example:

Test	Result

pragma table_info('Customers');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           CustomerID  INTEGER     0                       0
1           Name        TEXT        0                       0
2           Email       TEXT        0                       0
3           JoinDate    DATETIME    0                       0

Answer:(penalty regime: 0 %)

CREATE TABLE Customers(
CustomerID  INTEGER,
Name  TEXT,
Email  TEXT,
JoinDate  DATETIME
);

**Output:**

![Screenshot (92)](https://github.com/user-attachments/assets/44370246-f7ba-4d0a-b66c-295ad6320ca0)

**Question 5**
Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'

For example:

Test Result

INSERT INTO Student_details (RollNo, Name, Gender, Subject, email) 
VALUES (1, 'John Doe', 'M', 'Math', 'john@example.com');
select * from Student_details;
RollN  Name   Gen  Subject     email
-----  -----  ---  ----------  ----------------
1      John   M    Math        john@example.com

Answer:(penalty regime: 0 %)
ALTER TABLE Student_details 
ADD COLUMN email TEXT  not NULL default'Invalid';

**Output:**

![Screenshot (93)](https://github.com/user-attachments/assets/3a43d180-236e-4695-9a2e-e72237c54585)

**Question 6**
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

For example:

Test Result

INSERT INTO Orders (OrderID, OrderDate, CustomerID) VALUES (1, '2024-08-01', 1);
INSERT INTO Invoices (InvoiceID, InvoiceDate, Amount, DueDate, OrderID) VALUES (1, '2024-08-01', 100.0, '2024-09-01', 1);
SELECT * FROM Invoices;
InvoiceID   InvoiceDate  Amount      DueDate     OrderID
----------  -----------  ----------  ----------  ----------
1           2024-08-01   100.0       2024-09-01  1

Answer:(penalty regime: 0 %)

CREATE TABLE Invoices(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
Amount REAL CHECK(Amount>=0),
DueDate DATE CHECK(DueDate>=InvoiceDate),
OrderID INTEGER,
foreign key (OrderID) references Orders(OrderID)
);
**Output:**

![Screenshot (94)](https://github.com/user-attachments/assets/bfc153ea-4b96-4576-8021-db5521c03982)


**Question 7**
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

For example:

Test	Result

INSERT INTO Products
VALUES (1, NULL,0,5);

Error: NOT NULL constraint failed: Products.ProductName

Answer:(penalty regime: 0 %)

CREATE TABLE Products(
ProductID INTEGER primary key,
ProductName not NULL,
Price REAL CHECK (Price>0),
Stock INTEGER CHECK (Stock>=0)
);

**Output:**
![Screenshot (95)](https://github.com/user-attachments/assets/02c5722a-7c1f-432a-9583-094600da53e3)


**Question 8**
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

For example:

Test Result

INSERT INTO Customers (CustomerID, FirstName, LastName, Email) VALUES (1, 'Alice', 'Johnson', 'alice.johnson@example.com');
INSERT INTO Orders (OrderID, OrderDate, CustomerID) VALUES (1, '2024-08-01', 1);
select * from orders;
OrderID     OrderDate   CustomerID
----------  ----------  ----------
1           2024-08-01  1

Answer:(penalty regime: 0 %)

CREATE TABLE Orders(
OrderID INTEGER primary key,
OrderDate DATE not NULL,
CustomerID INTEGER,
foreign key (CustomerID) references Customers(CustomerID)
);

**Output:**

![Screenshot (96)](https://github.com/user-attachments/assets/6da774c1-b3b3-43f6-92a3-b0435421050f)


**Question 9**
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

For example:

Test	Result

INSERT INTO Department (DepartmentID, DepartmentName, Location) VALUES (1, 'Human Resources', 'New York');
select * from Department;
DepartmentID  DepartmentName   Location
------------  ---------------  ----------
1             Human Resources  New York

Answer:(penalty regime: 0 %)

CREATE TABLE Department(
DepartmentID INTEGER primary key,
DepartmentName TEXT UNIQUE  not NULL,
Location TEXT
);

**Output:**

![Screenshot (97)](https://github.com/user-attachments/assets/797b889f-8fe2-408b-9284-2596bcf0c619)


**Question 10**
In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

ISBN             Title                      Author           Publisher   Year
---------------  -------------------------  ---------------  ----------  ----------
978-1234567890   Introduction to AI         John Doe
978-9876543210   Deep Learning              Jane Doe         TechPress   2022
978-1122334455   Cybersecurity Essentials   Alice Smith                  2021
For example:

Test	Result

SELECT * FROM Books;

ISBN             Title                      Author           Publisher   Year
---------------  -------------------------  ---------------  ----------  ----------
978-1234567890   Introduction to AI         John Doe
978-9876543210   Deep Learning              Jane Doe         TechPress   2022
978-1122334455   Cybersecurity Essentials   Alice Smith                  2021

Answer:(penalty regime: 0 %)

INSERT INTO Books(ISBN, Title, Author, Publisher, Year)
VALUES('978-1234567890', 'Introduction to AI', 'John Doe', null, null);
INSERT INTO Books(ISBN, Title, Author, Publisher, Year)
VALUES('978-9876543210', 'Deep Learning', 'Jane Doe', 'TechPress', '2022');
INSERT INTO Books(ISBN, Title, Author, Publisher, Year)
VALUES('978-1122334455', 'Cybersecurity Essentials', 'Alice Smith', null, 2021);

**Output:**

![Screenshot (98)](https://github.com/user-attachments/assets/61f372c4-534d-464c-a325-2f12775804a8)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
