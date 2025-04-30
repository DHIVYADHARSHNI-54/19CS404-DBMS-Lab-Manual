# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
How many patients have expired insurance coverage for each insurance company?

Sample table:Insurance Table
![Screenshot (99)](https://github.com/user-attachments/assets/fe94df68-cb38-4201-8d85-3a04b34fafa1)

select InsuranceCompany,count(*) as TotalExpiredPatients

from Insurance

group by InsuranceCompany;


**Output:**

![Screenshot (100)](https://github.com/user-attachments/assets/f6876a60-51ea-4680-9b7e-a16757f199b7)


**Question 2**

How many prescriptions were written by each doctor?
Sample tablePrescriptions Table

![Screenshot (101)](https://github.com/user-attachments/assets/04f6765b-bc34-4ba2-a545-d088976a3190)

SELECT DoctorID,count(*) as TotalPrescriptions

from Prescriptions

group by DoctorID;


**Output:**

![Screenshot (102)](https://github.com/user-attachments/assets/d1852b8d-7935-4281-b85e-b1dddfad7197)


**Question 3**

What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table

![Screenshot (103)](https://github.com/user-attachments/assets/4935a868-df50-4e86-acd5-6d22f69e861b)

**Output:**

![image](https://github.com/user-attachments/assets/0a549ace-e896-4397-88e2-a63e0aa06f62)


**Question 4**

Write a SQL query to find the Fruit with the lowest available quantity.

![image](https://github.com/user-attachments/assets/ec9e01ee-cb01-4ad2-800d-1816eb3b26c2)

select name as fruit_name , min(inventory) as lowest_quantity

from fruits;

**Output:**


![image](https://github.com/user-attachments/assets/0204804f-612f-4252-b512-27c0a8b0a6d7)


**Question 5**

Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count. 

Note: Inventory attribute contains amount of fruits


![image](https://github.com/user-attachments/assets/fecec400-4e63-44ec-a54a-d0c5e0dfc04f)

select sum(inventory) as total_available_amount

from fruits

where price>0.5;

**Output:**

![image](https://github.com/user-attachments/assets/0e1afba4-9aee-4cc3-90b8-0cc8c04294fd)

**Question 6**

Write a SQL query to  find the average salary of all employees?


![image](https://github.com/user-attachments/assets/ecb34cbc-f30c-49f1-af27-f9ff4ab4602e)
`
select avg(income) as Average_Salary

from employee;

**Output:**


![image](https://github.com/user-attachments/assets/2da9bb45-675a-483a-8027-86a1ca7cb6cc)


**Question 7**

Write a SQL query to determine the number of customers who received at least one grade for their activity.


![image](https://github.com/user-attachments/assets/c413d6c9-76f1-4133-9406-5e8925e4c2b0)

SELECT COUNT(customer_id) AS COUNT

FROM customer

where grade is not null;

**Output:**


![image](https://github.com/user-attachments/assets/46ecfb3c-4382-48c0-abec-c48845b90daa)


**Question 8**

Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.


![image](https://github.com/user-attachments/assets/f0ed5434-0a3e-4c0b-9a95-3a6de1265359)

select category_id,sum(price) as Total_Cost

from products

group by category_id

having Total_Cost>50;


**Output:**


![image](https://github.com/user-attachments/assets/a26e2ca9-5a4e-4821-aaa2-e954e60ed2cd)


**Question 9**

Write a SQL query to find the difference between the maximum and minimum price of fruits?


![image](https://github.com/user-attachments/assets/50b4425e-f1e0-46a3-8042-683c97701287)

select (max(price)-min(price)) as price_diff

from fruits;


**Output:**


![image](https://github.com/user-attachments/assets/58551863-741a-4725-8727-48484a23f782)


**Question 10**

Write a SQL query to find the average length of names for people living in Chennai?


![image](https://github.com/user-attachments/assets/b2734a29-fd4a-42c0-b5bc-b0546b9db332)

select avg(length(name)) as avg_name_length

from customer

where city like '%Chennai%';

**Output:**


![image](https://github.com/user-attachments/assets/f74034bd-6685-48c2-a36b-789a47c1f104)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
