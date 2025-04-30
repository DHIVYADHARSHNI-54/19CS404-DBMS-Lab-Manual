# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**

Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

![image](https://github.com/user-attachments/assets/f0c06161-0ac3-4f15-b094-b01ead97bf82)

select medication_id as medic,medication_name,dosage

from Medications

where dosage=(select max(dosage)

from Medications
);

**Output:**

![image](https://github.com/user-attachments/assets/c1ff30f8-c5ef-463b-af94-8f6ac923e49d)

**Question 2**

Write a SQL query to List departments with names longer than the average length

Departments Table (attributes: department_id, department_name)

![image](https://github.com/user-attachments/assets/f2ef5e74-e8d0-4d25-8c6a-4650dcbe97f9)

select department_id, department_name

from Departments

where length(department_name)>(select avg(length(department_name))

from Departments
);


**Output:**

![image](https://github.com/user-attachments/assets/03fe021b-b21f-45de-9ceb-9cc675affbc1)


**Question 3**

Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

![image](https://github.com/user-attachments/assets/db7bc9a1-07e9-424c-8b65-59e1dd9dcea4)

select * from Employee

where age<(select avg(age)

from Employee

where income > 250000);

**Output:**

![image](https://github.com/user-attachments/assets/5c76a751-b74d-4edf-b676-eca43c863d91)

**Question 4**

From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

salesman table

![image](https://github.com/user-attachments/assets/7acc1eb6-7bd6-40da-91e2-6463b1af4e42)

select o.ord_no,o.purch_amt,o.ord_date,o.customer_id,o.salesman_id

from Orders as o

join Salesman as s on o.salesman_id=s.salesman_id

where s.name='Paul Adam';


**Output:**

![image](https://github.com/user-attachments/assets/41e6f8c4-7394-4e77-b3aa-d70e0f55ae7c)


**Question 5**

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

![image](https://github.com/user-attachments/assets/30b1007b-2f03-4c3f-be75-f6d18c04623b)

select * from CUSTOMERS

where salary in(select SALARY

from CUSTOMERS

where SALARY<2500
);

**Output:**

![image](https://github.com/user-attachments/assets/29fd533b-ec04-4c03-849d-05e84a253999)


**Question 6**

From the following tables write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count.

![image](https://github.com/user-attachments/assets/a102d6d1-2248-4a9f-8467-dbe2b851cb63)

select grade,COUNT(*)

from customer

where grade>(select avg(grade)

from customer

where city='New York'

)group by grade;

**Output:**

![image](https://github.com/user-attachments/assets/5105ad41-a38e-468f-8cc1-3c8c8e123c84)


**Question 7**

Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

![image](https://github.com/user-attachments/assets/3cecf462-1327-47bb-b668-61c393767586)

select g.student_id,g.student_name,g.subject,g.grade

from GRADES as g

where g.grade=(select max(grade)

from GRADES

where subject=g.subject)

order by g.student_name,g.grade;

**Output:**

![image](https://github.com/user-attachments/assets/bb43d47b-e5ba-40d7-a854-c4667803f562)

**Question 8**

Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

![image](https://github.com/user-attachments/assets/86382e4d-7f0f-48df-9e9d-1348e26f6f0e)

select g.student_name,g.grade

from GRADES as g

where g.grade=(select min(grade)

from GRADES

where subject=g.subject)

order by g.student_name,g.grade;

**Output:**

![image](https://github.com/user-attachments/assets/d3041b6a-831e-4e33-adbc-c4859d68b7fc)

**Question 9**

Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

![image](https://github.com/user-attachments/assets/f7f539e8-940b-462e-b790-40b2be3ec567)

select *from customer where customer_id=(select(salesman_id-2001)

from salesman

where name='Mc Lyon'
);


**Output:**

![image](https://github.com/user-attachments/assets/e03bc977-6d04-412b-a25b-7a72b86e85b2)


**Question 10**

From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

![image](https://github.com/user-attachments/assets/96c14708-a142-470a-b74b-9dc27d0ea58f)

select ord_no,purch_amt,ord_date,customer_id,salesman_id

from ORDERS

where purch_amt>(select avg(purch_amt)

from ORDERS

where ord_date='2012-10-10'
);


**Output:**

![image](https://github.com/user-attachments/assets/7524fe03-33a7-425e-a74c-c31994ebf8ff)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
