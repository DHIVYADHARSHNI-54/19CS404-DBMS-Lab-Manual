![Screenshot (113)](https://github.com/user-attachments/assets/ecfeb1a7-e2a5-42ad-ae89-a64734de32c5)# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**

Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

![Screenshot (104)](https://github.com/user-attachments/assets/6e518ec5-0d22-40c0-bc0c-7248e8931784)

update PRODUCTS

set reorder_lvl=reorder_lvl*0.7

where product_name like '%cream%'

and quantity>reorder_lvl;

**Output:**

![Screenshot (105)](https://github.com/user-attachments/assets/a9d3f9ea-1560-41bf-b824-47167887e375)


**Question 2**
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

![Screenshot (106)](https://github.com/user-attachments/assets/203d15b0-ca4b-4ba6-b2e2-9961d5524bb3)

update Suppliers

set address= '58 Lakeview, Magnolia'

where supplier_id=5;

**Output:**

![Screenshot (107)](https://github.com/user-attachments/assets/dc261721-38fe-4697-b049-b965f72084d4)


**Question 3**

Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

![Screenshot (108)](https://github.com/user-attachments/assets/5c21396d-1c41-4492-ab82-77e1fe8a1608)

update Products

set sell_price=sell_price*1.15

where quantity<50

and supplier_id=10;


**Output:**

![Screenshot (109)](https://github.com/user-attachments/assets/00cc0731-6b6b-4e89-9025-4ee06f4dfb09)


**Question 4**

For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

![Screenshot (110)](https://github.com/user-attachments/assets/86fa964a-f305-4b87-a49c-0ce79c1a5a23)

update Products

set sell_price=sell_price*1.15

where quantity<50

and supplier_id=10;


**Output:**

![Screenshot (111)](https://github.com/user-attachments/assets/4840874f-663e-4619-86f8-e28c2403249b)


**Question 5**

For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

![Screenshot (112)](https://github.com/user-attachments/assets/05b68bb7-3fff-434b-ae1b-23e886199fd9)

update SALES

set sell_price=sell_price+3

where product_id in(select product_id

from PRODUCTS

where supplier_id=4
);


**Output:**

![Screenshot (113)](https://github.com/user-attachments/assets/6d945d6b-ce75-4272-abd3-0d9b6a3bea2d)


**Question 6**

Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

![Screenshot (114)](https://github.com/user-attachments/assets/26784174-1330-4bc0-bd3e-a6c08ba833f9)

UPDATE Employees

set salary=salary*2

where department_id=20

and job_id like '%MAN';


**Output:**

![Screenshot (115)](https://github.com/user-attachments/assets/8df38546-62f7-4ab3-a2dd-90f7ab0d0889)


**Question 7**

Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

![Screenshot (116)](https://github.com/user-attachments/assets/763d66e5-ef23-41f1-ad94-dc958b78bc57)

delete from Surgeries

where surgery_date='2024-02-28';


**Output:**

![Screenshot (117)](https://github.com/user-attachments/assets/c5fde552-7a1f-4fac-8dcf-587597b4410c)

**Question 8**

Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

![Screenshot (118)](https://github.com/user-attachments/assets/ce497207-8f15-4929-8681-cad0df62bf5a)

delete from Customer

where CUST_CITY!='New York'

and OUTSTANDING_AMT>5000;

**Output:**

![Screenshot (119)](https://github.com/user-attachments/assets/4aab5d15-b963-4853-87ed-6b5b55073787)


**Question 9**

Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

![Screenshot (120)](https://github.com/user-attachments/assets/14c8cd5f-8a85-452b-8963-598f0d375646)

delete from Doctors

where Specialization in ('Pediatrics','Cardiology')

and last_name like '%Brown%';


**Output:**

![Screenshot (121)](https://github.com/user-attachments/assets/ce2d8eb3-63e6-4479-967b-ad0de44c5ba9)

**Question 10**

Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

![Screenshot (122)](https://github.com/user-attachments/assets/3292d209-8ebe-4561-b182-ce643eeb86a9)

delete from Customer

where GRADE>=2;


**Output:**

![Screenshot (123)](https://github.com/user-attachments/assets/b7341336-f945-4181-806f-9e96dfbe9392)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
