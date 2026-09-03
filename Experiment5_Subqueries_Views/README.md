# Experiment 5: Subqueries and Views
# NAME : LEKHASHRI E
# Register no : 212225230150
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
--
From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Note: date should be yyyy-mm-dd format

ORDERS TABLE

name            type
----------     ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int

```sql
select * from orders where purch_amt > (select avg(purch_amt) from orders where ord_date = '2012-10-10');
```

**Output:**

<img width="1227" height="485" alt="image" src="https://github.com/user-attachments/assets/fceb5223-97ce-47ab-9911-0d681ddb8f89" />

**Question 2**
---
Write a SQL query to List departments with names longer than the average length

Departments Table (attributes: department_id, department_name)

<img width="866" height="134" alt="image" src="https://github.com/user-attachments/assets/410fc693-d73f-4f29-b691-48d59153f770" />

```sql
select department_id as depar,department_name from Departments where length(department_name)>(
select avg(length(department_name)) from Departments);
```

**Output:**

<img width="762" height="442" alt="image" src="https://github.com/user-attachments/assets/747f6ebc-5622-46e8-a35d-c2d8b549c171" />

**Question 3**
---
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

<img width="602" height="233" alt="image" src="https://github.com/user-attachments/assets/00e14b43-3c41-47c6-ad9c-124bab5fbb0b" />


```sql
SELECT student_id,student_name,subject,grade
from GRADES
where (subject,grade) in(
select subject,min(grade)
from GRADES
group by subject);
```

**Output:**

<img width="1252" height="462" alt="image" src="https://github.com/user-attachments/assets/52806276-c383-4840-9d4b-c97b79dbab70" />

**Question 4**
---
From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
 
```sql
SELECT*
FROM Orders
WHERE salesman_id=(SELECT salesman_id FROM Salesman WHERE NAME='Paul Adam');
```

**Output:**

<img width="1197" height="412" alt="image" src="https://github.com/user-attachments/assets/c828c9a5-449c-4062-8aac-945391e86675" />

**Question 5**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

customer table

name         type
-----------  ----------
customer_id  int
cust_name    text
city         text
grade        int
salesman_id  int

```sql
select * from customer where customer_id=(select salesman_id from salesman where name='Mc Lyon')-2001;
```

**Output:**

<img width="1237" height="347" alt="image" src="https://github.com/user-attachments/assets/7b19b19b-a39d-4154-98b8-8f420e106a0e" />


**Question 6**
---
From the following tables write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count.

customer table

name         type
-----------  ----------
customer_id  int
cust_name    text
city         text
grade        int
salesman_id  int

```sql
select grade,COUNT(*) from customer
GROUP BY grade
HAVING grade>(select AVG(grade) 
from customer 
where city='New York');
```

**Output:**

<img width="811" height="390" alt="image" src="https://github.com/user-attachments/assets/d2e7c7b8-fd4a-42c9-9b72-de60e47a651a" />


**Question 7**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

name             type

------------   ---------------

id                    INTEGER

name              TEXT

age                 INTEGER

city                 TEXT

income           INTEGER

```sql
select * from employee where age<(select avg(age) from employee where income>250000);
```

**Output:**

<img width="1282" height="542" alt="image" src="https://github.com/user-attachments/assets/e415919d-00c9-44fd-b206-4586d5067e6d" />


**Question 8**
---
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

<img width="602" height="233" alt="image" src="https://github.com/user-attachments/assets/ba090731-ac01-4552-8841-d042c99eb633" />

```sql
SELECT student_name,grade
FROM GRADES G1
WHERE grade=(SELECT MIN(grade) FROM GRADES G2 WHERE G1.subject=G2.subject);
```

**Output:**

<img width="833" height="473" alt="image" src="https://github.com/user-attachments/assets/2c1a009c-404d-4003-9f93-7faa28bc076f" />


**Question 9**
---
From the following tables, write a SQL query to determine the commission of the salespeople in Paris. Return commission.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

customer table

name         type
-----------  ----------
customer_id  int
cust_name    text
city         text
grade        int
salesman_id  int

```sql
select commission
from Salesman
where salesman_id IN (
select salesman_id
from Customer
where city="Paris"
)
```

**Output:**

<img width="561" height="370" alt="image" src="https://github.com/user-attachments/assets/4e83e76a-8862-46e9-b57f-769fd9f41186" />

**Question 10**
---
From the following tables write a SQL query to find all orders generated by New York-based salespeople. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int

```sql
SELECT *
FROM orders
WHERE salesman_id IN(SELECT
salesman_id FROM salesman WHERE city='New York');
```

**Output:**

<img width="1295" height="410" alt="image" src="https://github.com/user-attachments/assets/8dadc1d8-9200-4edd-a699-b6e502167f63" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
