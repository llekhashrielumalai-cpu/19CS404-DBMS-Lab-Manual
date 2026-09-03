# Experiment 4: Aggregate Functions, Group By and Having Clause
# NAME : LEKHASHRI E
# Register no : 212225230150
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
--
How many patients are there in each age group category (e.g., under 20, 20-30, 30-40, etc.)?

Sample table: Patients Table

<img width="1076" height="161" alt="image" src="https://github.com/user-attachments/assets/21d547c4-0667-4509-8f5e-932e9b291700" />


```sql
SELECT
    CASE
        WHEN (
            CAST(strftime('%Y', 'now') AS INTEGER)
            - CAST(strftime('%Y', DateOfBirth) AS INTEGER)
            - (strftime('%m-%d', 'now') < strftime('%m-%d', DateOfBirth))
        ) < 20 THEN 'Under 20'

        WHEN (
            CAST(strftime('%Y', 'now') AS INTEGER)
            - CAST(strftime('%Y', DateOfBirth) AS INTEGER)
            - (strftime('%m-%d', 'now') < strftime('%m-%d', DateOfBirth))
        ) BETWEEN 20 AND 30 THEN '20-30'

        WHEN (
            CAST(strftime('%Y', 'now') AS INTEGER)
            - CAST(strftime('%Y', DateOfBirth) AS INTEGER)
            - (strftime('%m-%d', 'now') < strftime('%m-%d', DateOfBirth))
        ) BETWEEN 31 AND 40 THEN '31-40'

        WHEN (
            CAST(strftime('%Y', 'now') AS INTEGER)
            - CAST(strftime('%Y', DateOfBirth) AS INTEGER)
            - (strftime('%m-%d', 'now') < strftime('%m-%d', DateOfBirth))
        ) BETWEEN 41 AND 50 THEN '41-50'

        ELSE 'Above 50'
    END AS AgeGroup,

    COUNT(*) AS TotalPatients

FROM Patients

GROUP BY AgeGroup

ORDER BY
    CASE AgeGroup
        WHEN 'Under 20' THEN 1
        WHEN '20-30' THEN 2
        WHEN '31-40' THEN 3
        WHEN '41-50' THEN 4
        WHEN 'Above 50' THEN 5
    END;
```

**Output:**

<img width="891" height="495" alt="image" src="https://github.com/user-attachments/assets/7ac67ad3-d790-4864-86b0-2ba47d7b7d2c" />


**Question 2**
---
How many appointments are scheduled for each patient?

Sample table: Appointments Table

name                  type
--------------------  ----------
AppointmentID         INTEGER
PatientID             INTEGER
DoctorID              INTEGER
AppointmentDateTime   DATETIME
Purpose               TEXT
Status                TEXT

```sql
SELECT PatientID,COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY PatientID;
```

**Output:**

<img width="1045" height="647" alt="image" src="https://github.com/user-attachments/assets/5a999885-86c8-45a2-b87a-8f4f68582761" />


**Question 3**
---
How many prescriptions were written for each medication?

Sample tablePrescriptions Table

<img width="1082" height="154" alt="image" src="https://github.com/user-attachments/assets/50b5fd14-4702-4495-b034-110ee2367827" />

```sql
SELECT Medication, COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

<img width="1056" height="757" alt="image" src="https://github.com/user-attachments/assets/a4405647-c4e1-4cfb-818a-59ff0eea530d" />


**Question 4**
---
Write a SQL query to calculate the total number of working hours of all employees

Sample table: employee1

<img width="685" height="139" alt="image" src="https://github.com/user-attachments/assets/a7ff72cd-1266-43e2-b722-0fea50d9da74" />

```sql
SELECT SUM(workhour) AS "Total working hours"
FROM employee1;
```

**Output:**

<img width="772" height="360" alt="image" src="https://github.com/user-attachments/assets/93512856-609d-42d0-acfe-96cddf2a6749" />


**Question 5**
---
Write a SQL query to find  how many employees work in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
select count(id) as employees_in_california
from employee
where city like '%California%';
```

**Output:**

<img width="872" height="362" alt="image" src="https://github.com/user-attachments/assets/ed20259d-856e-4dd4-93f2-cea7a5c6f245" />


**Question 6**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002
```sql
select count(*) as COUNT
from customer;
```

**Output:**

<img width="796" height="358" alt="image" src="https://github.com/user-attachments/assets/a33cf0ec-aeeb-4398-8eaf-2dfa46f8dde5" />


**Question 7**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer

<img width="668" height="138" alt="image" src="https://github.com/user-attachments/assets/372408f8-5315-4b8d-b9c9-865e239f10ee" />


```sql
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city = "Noida"
```

**Output:**

<img width="817" height="365" alt="image" src="https://github.com/user-attachments/assets/fbf255cd-c2f5-43e0-884d-31e49047c4b1" />


**Question 8**
---
Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.

Sample table: products

<img width="972" height="212" alt="image" src="https://github.com/user-attachments/assets/53c5b1e3-387a-4139-a9b4-65389d91aeea" />


```sql
SELECT category_id, count(product_name) AS COUNT
FROM products
GROUP BY category_id
HAVING category_id > 2
```

**Output:**

<img width="900" height="391" alt="image" src="https://github.com/user-attachments/assets/30f94b43-a836-4665-a07b-a21ffd57e4d9" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

Sample table: employee

<img width="1011" height="215" alt="image" src="https://github.com/user-attachments/assets/158b6ed1-64ec-4e28-8dde-d34b15af8673" />

```sql
select city, sum(Income) as Income
from employee
group by city
having sum(Income) > 200000;
```

**Output:**

<img width="715" height="550" alt="image" src="https://github.com/user-attachments/assets/d6a2a1da-6c6c-40a8-8e96-fcabc7c78db1" />


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.

Sample table: employee

<img width="1011" height="215" alt="image" src="https://github.com/user-attachments/assets/792ff456-1b33-4b5d-9619-1906eec61d18" />


```sql
SELECT age, AVG(income) AS "AVG(income)"
FROM employee
GROUP BY age
HAVING AVG(income) BETWEEN 300000 AND 500000;
```

**Output:**

<img width="736" height="396" alt="image" src="https://github.com/user-attachments/assets/3e7c477c-c7a0-4b91-8927-cc2856ab9da5" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
