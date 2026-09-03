# Experiment 3: DML Commands
# NAME : LEKHASHRI E
# Register no : 212225230150
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
--
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE products SET sell_price=sell_price*1.10 WHERE category='Bakery';
```

**Output:**

<img width="1284" height="829" alt="image" src="https://github.com/user-attachments/assets/30f01472-fcdd-4244-9dbb-95ca20c4d00f" />


**Question 2**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```sql
UPDATE suppliers
SET supplier_name = UPPER(supplier_name)
WHERE contact_person LIKE '% Singh';
```

**Output:**

<img width="1276" height="707" alt="image" src="https://github.com/user-attachments/assets/5b07e1b2-ba18-4813-9e27-6874007788d9" />


**Question 3**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE Employees
set salary=salary*2
where department_id=20
and job_id like '%MAN';
```

**Output:**

<img width="1276" height="698" alt="image" src="https://github.com/user-attachments/assets/347c4d91-03af-447b-89cb-3ed8e4ec4cb7" />


**Question 4**
---
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT         

```sql
UPDATE products SET reorder_lvl = reorder_lvl-(reorder_lvl * 0.3) 
WHERE cost_price > 50 AND quantity < 100;
```

**Output:**

<img width="1275" height="772" alt="image" src="https://github.com/user-attachments/assets/a0f43bef-94fe-48da-a873-7ee761dd25c3" />


**Question 5**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE products
SET reorder_lvl = 40
WHERE category = 'Grocery';
```

**Output:**

<img width="1273" height="736" alt="image" src="https://github.com/user-attachments/assets/52b13909-49a6-46ac-8da9-b8b6da67afec" />


**Question 6**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```sql
delete from doctors
where last_name is null;
```

**Output:**

<img width="1275" height="845" alt="image" src="https://github.com/user-attachments/assets/4c67390c-ffa2-4869-a831-56fc8d7462c3" />


**Question 7**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3 or surgeon ID is 4.

Sample table: Surgeries
<img width="665" height="148" alt="image" src="https://github.com/user-attachments/assets/9300ac01-d4fc-46c7-b6f4-967ede04cac3" />

```sql
DELETE FROM surgeries
WHERE surgery_id = 3
OR surgeon_id = 4;
```

**Output:**

<img width="1267" height="839" alt="image" src="https://github.com/user-attachments/assets/dec0ffb2-be80-455a-b9a1-eca350d7f07d" />


**Question 8**
---
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors
WHERE last_name = 'Brown'
AND specialization IN ('Pediatrics', 'Cardiology');
```

**Output:**

<img width="1278" height="840" alt="image" src="https://github.com/user-attachments/assets/cbac244d-ac61-4981-92c0-d3a4f12bd181" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```sql
DELETE FROM Customer WHERE GRADE!=3;
```

**Output:**

<img width="1369" height="832" alt="image" src="https://github.com/user-attachments/assets/9a0bef92-1e11-418f-96de-8cc79d904dc9" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
DELETE FROM customer
WHERE LENGTH(CUST_NAME) = 6;
```

**Output:**

<img width="1274" height="847" alt="image" src="https://github.com/user-attachments/assets/9ed391dc-6e45-4026-8333-24709aaa70be" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
