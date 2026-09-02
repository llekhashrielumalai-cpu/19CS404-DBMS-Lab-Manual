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
-- Paste Question 1 here
<img width="921" height="485" alt="image" src="https://github.com/user-attachments/assets/33b6ede1-43f9-4ec8-8af5-1365d0cf27d3" />
```sql
<img width="508" height="131" alt="image" src="https://github.com/user-attachments/assets/93007b69-a19e-4c64-9430-01e2fbac0676" />
```

**Output:**



<img width="943" height="392" alt="image" src="https://github.com/user-attachments/assets/0c070242-2645-418e-9b41-787c9ccb5b27" />


**Question 2**
---
-- Paste Question 2 here
<img width="896" height="207" alt="image" src="https://github.com/user-attachments/assets/c750ebba-b2e6-40e9-9d5a-ab8885d2083d" />


```sql
-- Paste your SQL code below for Question 2
<img width="578" height="155" alt="image" src="https://github.com/user-attachments/assets/7fa3e3e7-2956-4dbd-8d4b-2317624d17c1" />


```

**Output:**

<img width="907" height="184" alt="image" src="https://github.com/user-attachments/assets/e42952b1-bbb0-4426-87d0-77e2b59ed93e" />


**Question 3**
---
-- Paste Question 3 here
<img width="794" height="318" alt="image" src="https://github.com/user-attachments/assets/63588cdd-64e0-4cc2-aee0-f83aa2e56ac5" />

```sql
-- Paste your SQL code below for Question 3
<img width="316" height="180" alt="image" src="https://github.com/user-attachments/assets/68233394-d963-4bb9-a536-2b4b2e7dfff5" />
```

**Output:**

<img width="906" height="289" alt="image" src="https://github.com/user-attachments/assets/3d37acf7-509b-48f2-bf63-5d160c169e93" />


**Question 4**
---
-- Paste Question 4 here
<img width="760" height="301" alt="image" src="https://github.com/user-attachments/assets/4fbf9649-e176-453e-a194-eff9de5c7f5e" />

```sql
-- Paste your SQL code below for Question 4
<img width="341" height="179" alt="image" src="https://github.com/user-attachments/assets/471e571c-7c49-4897-922a-5f2d5942f928" />

```

**Output:**

![Output4](output.png)
<img width="626" height="214" alt="image" src="https://github.com/user-attachments/assets/6642d2b0-0d3c-40e1-995b-061a21a85dfb" />

**Question 5**
---
-- Paste Question 5 here
<img width="633" height="362" alt="image" src="https://github.com/user-attachments/assets/a4753e34-3359-4540-92da-84a8bf8b0590" />

```sql
-- Paste your SQL code below for Question 5
<img width="441" height="186" alt="image" src="https://github.com/user-attachments/assets/26bebfc7-f02f-4fd1-9a40-09b8225f45e8" />

```

**Output:**
<img width="622" height="270" alt="image" src="https://github.com/user-attachments/assets/cfe47a25-7dbd-438d-b018-885867c70bd2" />

![Output5](output.png)

**Question 6**
---
-- Paste Question 6 here
<img width="658" height="391" alt="image" src="https://github.com/user-attachments/assets/8320eaf8-e600-4c0d-b586-0c409e240232" />

```sql
<img width="582" height="196" alt="image" src="https://github.com/user-attachments/assets/c8025f2d-db1e-4efa-842f-58d400eeb2cd" />

-- Paste your SQL code below for Question 6
<img width="622" height="218" alt="image" src="https://github.com/user-attachments/assets/938650fa-311f-491f-9e70-888efbf3fa64" />

```

**Output:**
<img width="582" height="171" alt="image" src="https://github.com/user-attachments/assets/56d3c7e7-29cd-4438-a961-9612d3e49cd5" />

![Output6](output.png)

**Question 7**
---
-- Paste Question 7 here
<img width="630" height="352" alt="image" src="https://github.com/user-attachments/assets/5659981e-018c-494a-be5f-2da3a12a2b92" />

```sql
<img width="518" height="216" alt="image" src="https://github.com/user-attachments/assets/d5f00805-3399-4415-94dc-3cc9b93804c9" />

-- Paste your SQL code below for Question 7
```

**Output:**
<img width="622" height="325" alt="image" src="https://github.com/user-attachments/assets/72647efe-6ed1-4def-99ee-84cae5f5c64e" />

![Output7](output.png)

**Question 8**
---
-- Paste Question 8 here
<img width="638" height="224" alt="image" src="https://github.com/user-attachments/assets/caafeaac-4876-4905-b9db-942c8501aa83" />


```sql
<img width="526" height="190" alt="image" src="https://github.com/user-attachments/assets/c133db72-0514-42ee-9167-5387fb8c1a7a" />

-- Paste your SQL code below for Question 8
```

**Output:**
<img width="597" height="250" alt="image" src="https://github.com/user-attachments/assets/317d6cc4-fb53-4a45-b5c1-2bef9206dee6" />

![Output8](output.png)

**Question 9**
---
-- Paste Question 9 here
<img width="624" height="262" alt="image" src="https://github.com/user-attachments/assets/5e31a4b0-7d77-4ae7-8095-9a28ed6e5f57" />

```sql
<img width="446" height="71" alt="image" src="https://github.com/user-attachments/assets/6f9463df-3044-401f-9548-4344d868f174" />


```

**Output:**
<img width="605" height="211" alt="image" src="https://github.com/user-attachments/assets/f3a3fe48-f552-4848-acac-0bd534f200f6" />

![Output9](output.png)

**Question 10**
---
-- Paste Question 10 here
<img width="608" height="280" alt="image" src="https://github.com/user-attachments/assets/02d37c8e-1e3a-4703-8590-e18a4b2858bc" />

```sql




```

**Output:**

![Output10](output.png)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
