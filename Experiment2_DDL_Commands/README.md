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
-- Write a SQL statement to Update the grade of all customers in Chennai city as  5. 

```sql
-- UPDATE customer
SET grade=5
WHERE city = 'Chennai';
```

**Output:**
<img width="1172" height="387" alt="image" src="https://github.com/user-attachments/assets/b9dfce87-0b33-4a89-a4cc-6d5d20dd57fc" />

**Question 2**
---
-- Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

```sql
--UPDATE products
SET sell_price = sell_price*1.10
WHERE category = 'Bakery';
```

**Output:**

<img width="1282" height="290" alt="image" src="https://github.com/user-attachments/assets/fe98573c-50d8-4925-960a-ff5bf4bd8fd7" />


**Question 3**
---
--Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

```sql
UPDATE products
SET sell_price = ROUND(sell_price*1.10)
WHERE supplier_id=6;
```

**Output:**

<img width="1298" height="310" alt="image" src="https://github.com/user-attachments/assets/da8d0b5b-5b84-4729-9346-1b1d828d85bb" />


**Question 4**
---
-- Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'



```sql
UPDATE employees
SET salary=salary*2
WHERE department_id=20
AND job_id LIKE '%MAN';
```

**Output:**
<img width="1296" height="180" alt="image" src="https://github.com/user-attachments/assets/f9a69e1c-2ac0-4112-a1d9-36517b0986a5" />


**Question 5**
---
-- Write a SQL query to Delete All Doctors with a NULL Specialization

```sql
-- DELETE FROM doctors
WHERE specialization IS NULL;
```

**Output:**

<img width="838" height="418" alt="image" src="https://github.com/user-attachments/assets/fb19d6f4-611c-46be-8d5c-6bff6e1b6153" />

**Question 6**
---
-- Write a SQL query to determine the age group of value1 in the Calculations table as 'Child' if it is less than 13, 'Teen' if it is between 13 and 19, and 'Adult' if it is 20 or older.



```sql
-- SELECT 
     id,
     value1,
     CASE
         WHEN value1 < 13 THEN 'Child'
         WHEN value1 BETWEEN 13 AND 19 THEN 'Teen'
         ELSE 'Adult'
     END AS age_group
FROM Calculations;
```

**Output:**

<img width="509" height="193" alt="image" src="https://github.com/user-attachments/assets/32356797-e54c-4304-a22a-b0738c6c5084" />


**Question 7**
---
-- Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

```sql
DELETE FROM doctors
WHERE specialization = 'Pediatrics'
AND first_name = 'Michael';
```

**Output:**

<img width="865" height="211" alt="image" src="https://github.com/user-attachments/assets/420aa06b-296d-499a-99cf-e19ae9d27646" />


**Question 8**
---
-- Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

```sql
--DELETE FROM customer
WHERE cust_city LIKE 'L%';
```

**Output:**

<img width="1285" height="514" alt="image" src="https://github.com/user-attachments/assets/25f0dfd2-4430-4a39-b968-a07e49bf961a" />


**Question 9**
---
--  Write a query to fetch details of all employees excluding the employees with first names, “Sanjay” and “Sonia” from the EmployeeInfo table.


```sql
-- SELECT * FROM EmployeeInfo
WHERE EmpFname NOT IN ('Sanjay','Sonia');
```

**Output:**

<img width="1212" height="114" alt="image" src="https://github.com/user-attachments/assets/1c0e100c-1405-407a-84e1-ec6d0170b72b" />


**Question 10**
---
--Write a query to fetch all the records from the EmployeeInfo table ordered by EmpLname in descending order and Department in the ascending order.

```sql
--SELECT * FROM EMPLOYEEInfo
ORDER BY EmpFname DESC , Department ASC;
```

**Output:**

<img width="1263" height="160" alt="image" src="https://github.com/user-attachments/assets/1fff51f3-197d-447d-a56c-72d71cdbd5b1" />

<img width="1918" height="550" alt="image" src="https://github.com/user-attachments/assets/4dff6b36-74b7-4b85-9f2b-00a57cfbdb35" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
