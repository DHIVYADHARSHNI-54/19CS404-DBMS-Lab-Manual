# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**

From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

Sample table: orders

![image](https://github.com/user-attachments/assets/923613e4-50bf-422b-bf64-005ccb658f7d)

select o.ord_no,

o.ord_date,

o.purch_amt,

c.cust_name as 'Customer Name',


c.grade,

s.name as Salesman,

s.commission

from orders as o

join customer c on o.customer_id=c.customer_id

join salesman s on o.salesman_id=s.salesman_id;


**Output:**

![image](https://github.com/user-attachments/assets/03577f03-803c-4da2-9d03-97aa3f9a0a51)


**Question 2**

write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

![image](https://github.com/user-attachments/assets/9ed2ef85-306f-4d7c-9b28-e494ff379b2c)

select s.name as Salesman,c.cust_name,c.city

from salesman s

join customer c on s.city=c.city;


**Output:**

![image](https://github.com/user-attachments/assets/1514cec3-4147-48a5-be70-b8e8e09d6823)


**Question 3**

Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a null discharge date.

![image](https://github.com/user-attachments/assets/ffd39cd2-0199-4c24-b070-37adc1c2d961)

select p.first_name as "patient_name",d.first_name as doctor_name

from patients p

inner join doctors d on p.doctor_id=d.doctor_id

where p.discharge_date is null;

**Output:**

![image](https://github.com/user-attachments/assets/d77773e0-0bdd-41e5-976d-531bb5f686c8)

**Question 4**

Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'New York'.

![image](https://github.com/user-attachments/assets/ce45e882-539a-44c5-8506-9ab6dc1076f2)

select s.name

from salesman s

left join customer c on s.salesman_id=c.salesman_id

where c.city='New York';


**Output:**

![image](https://github.com/user-attachments/assets/c4b1f971-73f6-4a51-93ba-7e8a9d7cd1b1)

**Question 5**

From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

Sample table: customer

![image](https://github.com/user-attachments/assets/82b016b3-f1cd-4892-b9ce-c2b7bb414d77)

select c.cust_name,

c.city,

c.grade,

s.name AS Salesman,

s.city 

from customer c

join salesman as s ON s.salesman_id=c.salesman_id

order by customer_id ASC;


**Output:**

![image](https://github.com/user-attachments/assets/e3de8e7b-53f9-4a94-b416-81e21953eae5)


**Question 6**

Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.

![image](https://github.com/user-attachments/assets/9ca00b70-18ac-444c-901e-2732d42f06ed)

select c.cust_name,

c.city,

o.ord_no,

o.ord_date,

o.purch_amt

from customer c

left join orders o ON c.customer_id=o.customer_id

where c.city = 'London';


**Output:**

![image](https://github.com/user-attachments/assets/a7cc49bb-a008-4677-83dd-f8e8358dbd02)

**Question 7**

Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n") and the "department_name" column from the "departments" table, with an inner join on the "department_id" column.

NURSES TABLE:

![image](https://github.com/user-attachments/assets/26c98204-92c9-445b-8e11-a331378449ec)

d.department_name

from nurses n

inner join departments d ON n.department_id=d.department_id;

**Output:**

![image](https://github.com/user-attachments/assets/2b4d20a0-9e6d-4e62-bfdb-f26a460fb69f)


**Question 8**

From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission

![image](https://github.com/user-attachments/assets/5f4044f2-c4f2-43f3-afff-a530ac661d0f)

select c.cust_name AS "Customer Name",

c.city,

s.name as "Salesman",

s.commission

from customer c

inner join salesman s ON c.salesman_id=s.salesman_id;

**Output:**

![image](https://github.com/user-attachments/assets/12b26f35-9b14-46d1-a457-5f6b2447c653)


**Question 9**

Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

![image](https://github.com/user-attachments/assets/dd2cf953-8286-4f5d-b4bf-0d6b45be6f27)

select a.cust_name,a.city,b.ord_no,

b.ord_date,b.purch_amt as "Order Amount"

from customer a 

left outer join orders b  ON a.customer_id=b.customer_id

order by b.ord_date ;

**Output:**

![image](https://github.com/user-attachments/assets/784367a9-e8d8-4dfa-9402-ff8bf6230ec7)


**Question 10**

Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-02-01' and '2024-02-28'.

![image](https://github.com/user-attachments/assets/32711474-ef99-4ecd-8251-9e8a116d9280)

select p.*

from patients p

inner join appointments a ON p.patient_id =a.patient_id

where a.appointment_date BETWEEN 

'2024-02-01'AND '2024-02-28';


**Output:**

![image](https://github.com/user-attachments/assets/d4d9c35b-971c-42d3-8db7-930335e4a5f5)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
